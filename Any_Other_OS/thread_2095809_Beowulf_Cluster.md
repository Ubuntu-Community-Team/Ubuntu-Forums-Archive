---
title: "Beowulf Cluster"
date: 2012-12-18
forum: Any Other OS
---

### Post by coljohnhannibalsmith on 2012-12-18
Hello,

I've just heard about an exciting use of commodity grade PCs, the Beowulf cluster.

Frankly, I'm not sure what all they can be used for; but the thought of all that power under my command excites me and I want to learn more.  Can some of you fill me in on the uses of such a device and its limitations.  Also, what software will I need to run it.  I've heard of Cluster Knoppix, but what is the best?

Can a Beowulf Cluster be used for encryption and decryption?  Also, how about telecommunications switching?  My dream is to build a small volunteer run telecommunications system that can't be hacked, or very nearly so.  I believe we all have a right to our electronic privacy and anonymity and wish to devote myself to that goal.

Anyway, I don't even know if such a device would be appropriate for this task; but I find it intriguing.

Thanks Hannibal:D

[IMG]http://thenextasset.com/floorplan/jquery-mousewheel/images/beowulf-cluster-ubuntu-server-i0.jpg[/IMG]

---

### Post by QIII on 2012-12-18
It may be a "commodity" supercomputer, but you'd have to have a lot of commodity to make something that would do much.

I used to use KestrelHPC, but I don't know if it is still under active development.  It did work.  I used it on Debian.

[http://kestrelhpc.sourceforge.net/](http://kestrelhpc.sourceforge.net/)

---

### Post by coljohnhannibalsmith on 2012-12-24
I visited the link you provided; and I received the following message:

**Features**

                 
[LIST]
[*]                         **Debian/Ubuntu package.**

                                                      KestrelHPC is installed as a Debian package on your current system.
[*]If this is true how do I access it?
[*]I'm also aware of a project called SETI@Home, which uses distributed supercomputing to control what is essentially an infinite number of remote sensors.  Can a Beowulf cluster do this?
[/LIST]
BTW, how much commodity do I really need to accomplish something significant.  I'm aware of supercomputers such as "Blue Waters" with 300,000 cores and 1.9 Petaflops of RAM.


Thanks Hannibal

---

### Post by Bandit on 2012-12-25
A lot of factors go into a Beowulf cluster. Speed of Network is huge and how well the software is written to use the cluster. There are much more factors but those two are the biggest. 

See what a Beowulf cluster does is take segments of data, send them to a machine that is idle and let it process that segment. So if you have say a dozen PCs on your cluster, it will try to break the data up and split the processing up over those 12 PCs. Thus it doesnt make your computer any faster say playing a game, but for something like medical systems that analyze DNA for example. Those computers can take those segments, process them and send back the processed data were the main system will reassemble the data and give you processed information as a whole.  So depending on how the software is written to work with clusters and how many segments-vs-computers (or nodes as they are often called) determines how much faster the data results can be.

So in the long run while as awesome as it would be to have a Beodog sitting in your room. The likely hood you would have software to take advantage of it is rare. Unless your a SETI at home fanatic.

---

