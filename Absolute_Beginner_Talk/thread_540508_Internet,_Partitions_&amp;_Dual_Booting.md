---
title: "Internet, Partitions &amp; Dual Booting"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by floaton on 2007-09-01
I am trying to dual boot a laptop that I have had for a couple of years.  I have backed everything up and defraged recently.  I have a Compaq R4000 100Gb harddrive with about 30 Gb free space.  AMD 64 Althon processor.  512Mb RAM.  Using the 7.04 live CD I am having the following problems:

1)  When just in live mode, I can not connect to the internet.  I have gone through the pppoeconf set up, but still no internet. 

2)  Do I need to partition the disk before the install?  I was under the impression that a the partition manager in the install would cover that with the Guided - partition use free space bit.  When I try that, it says that I have insufficient space.

I guess that it is for now.  Thanks for the help.

---

### Post by goatflyer on 2007-09-01
1) I don't know what kind of ethernet card you have., open a terminal window and type
```

lspci

```
and read the output to find what type of network card you have.  Then launch a seperate help thread for just that problem.


2) Try to install using the manual partition option.  You definitely don't want all the freespace going to ubuntuu otherwise windows won't work too well.   Here are my humble recommendation for your 30G  when manually partitioning.

Leave at least 5GB freee space to the existing windows partition.
create a 2GB swap space
create a 2GB FAT partition for files read/writeable by both windows and ubuntu
create a 21GB root ("/")  for ubuntu


Depending on how you plan to use your laptop, or what flexibility you may want fo the future,
some people would suggest you create a seperate /home partition.  I did, but I had more freespace to play with that you do.  If you want this, I'd suggest leaving around 8GB for ubuntu depeding how much you plan to install. (I have a loaded box and everything fits fine in less than 5GB).  So for you, that would mean a 13 GB partition for /home, and the remaining 8GB for /

---

