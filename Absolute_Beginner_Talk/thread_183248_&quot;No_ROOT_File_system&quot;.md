---
title: "&quot;No ROOT File system&quot;"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Ichido on 2006-05-27
I have Linspire 5 on hda.
I am trying to install Ubuntu on hdb1 and Kubuntu on hdb2.
I have Partitioned my 2nd hard drive using QTParted as:

hdb1 ext3 12.39GB
hdb2 ext3 12.39GB
hdb3 Linux-Swap 534MB
hdb4 ext3 12.3GB

After this I only get the ERROR: "No ROOT File System".
I don't understand what it's asking for!?
What I'm I doing wrong?](*,)

---

### Post by Koech on 2006-05-27
Yes, you didn't specify the location of / root filesystem, which is usually ext2 in my case. Make sure as you edit partitio tables specify this.

---

### Post by mostwanted on 2006-05-27
One of the partitions need to refer to /

I don't understand how you're planning to install both Ubuntu and Kubuntu as two different operating systems at the same time. Just install Ubuntu regularly, then install kubuntu-desktop using Synaptic.

The GRUB that Ubuntu install won't find and set up Linspire, so you'll need to tinker with that afterwards.

---

### Post by johnc4510 on 2006-05-27
During the install when you get to the partitioning part, choose manual. Then choose the partion you want to install Ubuntu on and there will be a drop down list, choose /
This will be the root partion.

---

### Post by Ichido on 2006-05-27
I've been running Linspire For a year and it's SO Simple!!
I want to try other Linux Systems.
I can run Ubuntu and Kubuntu from the Live CDs so I thought I should Install both to expirement with.
Thanks for the Info.
I'll try it this week end.

---

### Post by Ichido on 2006-06-01
Thank You Koech, mostwanted & johnc4510:KS 
Ubuntu is now "Up & Running":)

---

