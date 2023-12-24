Evolution of Big Data Frameworks
In 2004 google published Mapreduce paper which fundamentally changed the way

we process distributed data.

Basically with Mapreduce the whole processing was getting done in two steps.

A map and a reduce phase.

Now google took this Mapreduce and continued to innovate more systems and papers over the

time but they were not an open source products and were not initially released publicly,

they were only being used at google internally within their systems.

And meanwhile at the same time, Open source communities like Apache took that MapReduce

paper and created Hadoop which was like a revolution in the Big data processing frameworks.

Hadoop used Mapreduce as base and started doing distributed processing as key value

pairs.

Now

even though It managed to provide Scalability and simplicity in distributed processing world

using low cost machines.

But sooner we realized that at core Mapreduce is just a single select and groupby.

Mapreduce worked well for the use cases which can be broken into a map and reduce phase

but for many real-world use cases, a chain of Map and reduce stages is required.

A chain of Mapreduce jobs means a lot of disk reads and writes, apparently increasing the

overall processing time.

That is why there was a need of a high-level API that can create a pipeline of operations

with less hdfs read, writes.

That’s what from where Flume arose.

Flume basically was the Orchestration and optimization of Mapreduce.

Rather than a single operation, flume creates a graph of multiple operations which eventually

get converted into an optimized series of Mapreduces without multiple hdfs writes.

Actually, later on it was Flume which emerged as the base programming model for Spark and

Flink as well.

Then we have Spark, a lightening fast processing engine which they promise to be 100 times

faster than Hadoop.

It supported both Batch and stream processing.

At core it does lazy evaluation of the program, creates a DAG of the code and then execute

it.

Spark streaming is also fast but it does not have any mechanism to handle late elements

or we can say out of order elements in a window. We will discuss what are these late elements

further in the course.

So, Spark was not prepared to Handle out of order elements which was later on addressed

by a new Apache product i.e.

Flink Flink was more or less same like Spark but

with more speed, performance and automated tuning.

It was actually the first engine which started considering a data stream as a first class

citizen and that is why it became a true stream processing engine.

But the major thing was its ability to handle out of order elements in a stream.

It had a lot of mechanisms like watermarking, states, triggers etc to do so.

In google side they had Millwheel created for the same thing.

Millwheel can be seen as Flink of Google or vice versa.

So this was how Apache evolved in its side with lot many other technologies like HBase,

a columnar database, Tez engine, Oozie for scheduling, hive etc.

Basically, Apache created a whole new open source ecosystem for end to end Big data processing

that came into being after Mapreduce.

Now coming towards google side.

Till 2014 google did not publish any of their papers or systems they were using internally,

but in 2014 google thought of creating a code rather than publishing a paper of it.

So by using all of its historical papers and systems, google created cloud dataflow as

a part of Google cloud platform GCP.

Cloud dataflow is a fully managed service for creating and executing optimized parallel

data processing pipelines.

It is basically both a programming model i.e. a SDK for writing data processing pipelines

and also fully managed service for executing them.So developing and executing them both.

Actually, cloud dataflow was the one which proposed unified batch and stream data processing.

Later on, Google provided the model and SDK to Apache in beginning of 2016 to create their own model

on top of it.

Now as you can see there are 2 separate worlds flourishing in their own zone.

These zones were isolated from each other and the components in them cannot integrate

with each other.

Means You cannot just create a spark scala code and run it using Google Cloud dataflow

OR vice versa, code created for Google Millwheel cannot be run on Apache’s engines.

Now what Beam is doing, Beam is bringing these 2 worlds together.

It is based on Dataflow programming model and generalising integrated with a broader

Big data ecosystem.

After this integration, you can now build language agnostic pipelines using Apache Beam

programming model and run it anywhere either on Open source runners or on Google cloud

dataflow.

Basically, it means if you write a code in Beam then it can be run on any of the Google’s

or Apache’s engines.

Moreover, Beam has also separated the tight integration of language SDks and its runners.

With this You can now choose any of the programming language that Beam supports, build pipelines using that language

and run it on any engine.

So create a beam program in any of your favourite language and run that program in any of your

favourite engine.