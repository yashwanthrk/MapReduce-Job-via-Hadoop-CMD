# MapReduce-Job-via-Hadoop-CMD
MapReduce is a programming model, and Hadoop is an open-source software framework that implements it for processing and generating large data sets. A MapReduce job in Hadoop involves a Map phase, which processes data chunks in parallel, and a Reduce phase, aggregating the map outputs into the final result. 



<a name="br1"></a> 

**Team members : Dhiraj Gunasheela Nikitha Sadhanandha, Rakshith Venkatesh Murthy Gowda,**

**Yashwanth Rama Krishna Reddy, Dhiraj**

**1.**

Created local instance of Hadoop

To check Hadoop health in command prompt



<a name="br2"></a> 

The `jps` command lists out all Java processes running on a machine, useful in Hadoop since its

services are Java processes. It aids in debugging by allowing you to verify if all Hadoop services (like

NameNode, DataNode, ResourceManager, etc.) are operational.



<a name="br3"></a> 

**Created dir phase-3**

**Loaded amazon review dataset to phase-3 using Hadoop File system put command, which does**

**write operation**

We have used textual dataset

**In simple terms, hdfs dfs -put command took 1.39 seconds to complete in real time which is 2x**

**faster than loading in pandas dataframe**



<a name="br4"></a> 

**2.**

**hadoop jar**

**/opt/homebrew/Cellar/hadoop/3.3.4/libexec/share/hadoop/mapreduce/hadoop-mapreduce-ex**

**amples-3.3.4.jar wordcount /phase-3/test.ft.txt /output**

**Performing mapreduce job on test.ft.txt dataset**



<a name="br5"></a> 

**Total time elapsed is 22 seconds which includes various factors mapping time, shuffling, inter**

**process communication, reduce tim.**

**Average Map Time (13 sec)**: This is the average time taken by the 'Map' function to process the

input data chunks and output key-value pairs. This includes breaking down the text into individual

words and emitting a key-value pair for each word, with the word as the key and '1' as the value.

**Average Shuffle Time (8 sec)**: This is the average time taken to perform the 'Shuffle & Sort' phase.

This phase collects the outputs from all the 'Map' tasks, sorts these key-value pairs based on the

keys (the words), and groups the values (counts) for each unique key together.

**Performing word count operation without mapreduce.**

**Couldn’t run the code, my system couldn’t handle the load and I had to restart the kernel**

**everytime**



<a name="br6"></a> 

3\.

MapReduce is essentially a programming paradigm that uses the power of parallel processing to

handle and analyze vast datasets efficiently. It operates on the principle of breaking down a large

task into smaller subtasks, which can be processed independently and parallelly

The MapReduce consists of three main stages: Map, Shuffle & Sort, and Reduce.

● **Map**: In this stage, the input data is divided into chunks and processed in parallel by multiple

worker nodes. Each worker applies a given function, called the "map function," to the input

data it receives. The map function transforms the input data into a set of intermediate

key-value pairs.

● **Shuffle & Sort**: Once the map stage is complete, the intermediate key-value pairs generated

by the workers are collected and sorted based on the keys. This sorting step is crucial to

ensure that all the values associated with a particular key are grouped together.

● **Reduce**: In the reduce stage, another set of worker nodes takes the sorted intermediate data

and applies a given function, called the "reduce function," to produce the final output. The

reduce function aggregates the values associated with each key and generates a set of final

output key-value pairs.

Throughout the MapReduce process, there are two key actors involved:

1\. Master: The master node coordinates the overall execution of the MapReduce job. It assigns map

and reduce tasks to the available worker nodes, monitors their progress, and manages the data

exchange between the workers.

2\. Workers: The worker nodes are responsible for performing the actual computation. They execute

the assigned map and reduce tasks on their allocated portions of the data. Each worker processes

its data independently of other workers.

**In the context of word count**

**Map phase**

● **Input**: The input data for the word count task is a collection of text documents.

● **Map function**: Each mapper processes a portion of the input data. The map function takes a

document as input and emits key-value pairs. The map function tokenizes the document into



<a name="br7"></a> 

individual words and emits a key-value pair for each word, where the word is the key and the

value is set to 1.

**Shuffle and Sort Phase**

● **Shuffle**: The MapReduce framework collects all the intermediate key-value pairs generated

by the map function and redistributes them based on the keys.

● **Sort**: Within each group, the intermediate key-value pairs are sorted based on the keys in

ascending order.

**Reduce phase**

● **Reduce function**: Each reducer takes a group of key-value pairs with the same key as input.

The reduce function receives a key (a word) and a list of values (a list of 1s).

**The final output of the MapReduce job is a collection of key-value pairs where the key represents**

**a unique word, and the value represents the total count of occurrences of that word across all the**

**input documents.**

Extra Credit



<a name="br8"></a> 


