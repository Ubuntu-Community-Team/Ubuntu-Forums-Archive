---
title: "[SOLVED] dual booting winXP and Ubuntu and the partitioning of drives"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by robinberghuys on 2008-01-23
Before I start installing Ubuntu, I think it would be a good idea to check here if it's possible at all. I have already had winXP Pro up and running for a while, and my HDD is partitioned into a C: (for Windows, programs and the like) and a D: (for My Documents, music and stuff like that). Is it possible to install Ubuntu on a third partition? I've never seen a HDD being partitioned into three parts. It might be useful to know that I'm intending to install Ubuntu onto an IBM/Lenovo Thinkpad T60p (which has Linux support according to [this]("http://www.lenovo.com/news/us/en/2006/08/t60p.html") and more specs can be found [here]("http://www.notebookreview.com/default.asp?newsID=2767").) So hopefully someone out there can helpme!

Thanks in advance!

---

### Post by poriggity on 2008-01-23
I used the Gnome partitioner on the install cd, and partitioned the hard drive into 3 parts, just lke you are wanting to do.  No problems yet.  I run XP pro on one partition, and ubuntu on the other.

---

### Post by robinberghuys on 2008-01-23
Alright! Well, I guess this answers my question. I'm glad it went this fast. Thanks!

---

### Post by KingWilliam on 2008-01-23
I don't know the exact amount of possible partitions, but you can make lots of em. Yo should know that Ubuntu might run better if you create an extra swap partition. But you will notice that during your installation. Your disk should become something like this:

Windows Partition | Data Partition | Ubuntu Partition | Swap

The Swap doesn't have to be big so you wont lose much disk capacity there. This should work perfectly. 
The fact you have that separate partition for data is actually a good thing. Because it will be an easy place to share files between your Linux and Windows. I have the same thing in my system. Only the data is a on separate physical drive.
Hope this was a push in the right direction...

---

### Post by robinberghuys on 2008-01-23
Yes it was, that's a great idea. Thanks!

---

### Post by Watchguy on 2008-01-23
Don't know if you saw this already but here's some extra reading as well. It was very informative for me anyway.


[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

