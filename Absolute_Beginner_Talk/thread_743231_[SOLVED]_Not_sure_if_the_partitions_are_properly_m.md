---
title: "[SOLVED] Not sure if the partitions are properly mounted"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Nyas on 2008-04-02
This might be the stupidest question I will ever ask, but I just want to make sure I did everything correctly.

It was my very first Ubuntu install on Dell Inspiron laptop, dual boot with Windows XP. I partitioned my disk with *ubiquity* like this:

sda1 NTFS /windows  
sda2 ext3 /
sda3 swap
sda5 ext3  /home  (logical)

The install went flawlessly and everything seems to be working properly right now, however I have not yet started working with this new system. 

In Windows *ext2 IFS* can see all the partitions and asign letters to them. I created a sample .txt file in H: disk (sda5) and it appeared in my home directory in Linux. 
In Ubuntu the *System Monitor* also shows all the partitions correctly. 

There is one thing that still confuses me though. Both /windows and /home appear under /. *My computer* in Ubuntu shows only CD drive and Filesystem that has a size of sda2. /windows and /home are inside it. They do not appear in *My Places* menu either.

The folder properties in Nautilus tells me this:

location /
volume /windows 

location /
volume /home

These two folders also have the size of sda1 and  sda5 respectively.

Are all the partitions correctly mounted and are separate? 
Or am I only confused by the graphical display in Nautilus? Why is sda5 (60GB) is displayed inside the root directory sda2 (30GB) then?

---

### Post by jken146 on 2008-04-02
The reason is the directory structure of Linux.  / is the highest level directory and **everything** else is inside / -- this includes mount points for any other partitions you have.  Each partition is mounted at a place in the file system, /dev/sda5 is mounted at /home.

In Linux, everything is a file and each file is somewhere in the file system, underneath /

---

### Post by Nyas on 2008-04-03
OK, now it makes more sense.
Thank you for the reply :)

---

