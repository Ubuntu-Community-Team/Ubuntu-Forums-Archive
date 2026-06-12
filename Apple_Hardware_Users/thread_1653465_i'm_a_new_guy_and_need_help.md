---
title: "i'm a new guy and need help"
date: 2010-12-26
forum: Apple Hardware Users
---

### Post by gaboguy7 on 2010-12-26
ok, so I'm new to ubuntu and am trying to install it to my macbook pro 6,2. the instructions say to install rEFIt, and i followed the instructions for that, but I don't understand what the Mac OS X installation volume is. help?

---

### Post by kgarbutt on 2010-12-26
It is the hard-drive of your mac computer.

---

### Post by gaboguy7 on 2010-12-27
ah i see. thanks!

---

### Post by gaboguy7 on 2010-12-27
ugh, first, sorry to be annoying by asking so many, probably obvious, questions. but here i go: i'm trying to install Ubuntu 10.10 from a CD that i downloaded from the Ubuntu site to my macbook pro 6,2 running the intel i5 processor. when I go to install, the [instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu")  say that you should click "specify partitions manually (advanced)" if the option "install to largest continuous free space" is not available (which it wasn't). So i clicked it and followed the instructions but I have some questions about them First, the instructions say to create two new partitions (in the free space i'm assuming, correct me if I'm wrong on any of this). So i do but I don't know whether to put it at the beginning or the end of the disk, or whether or not it matters. second, when I go to create the second partition, the [instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu") say to make it an EXT4 (which was not problem) but then it says "in the mount point drop-down menu, select /.FIXME: Image1, creating a swapspace FIXME: Image 2, a finished partitioning scheme." However, the mount point selection /.FIXME: Image1 is no available (in fact, no version of /.FIXME is available at all!) so i just named it that, but then the swap space /FIXME: Image2 isn't created, and when I try to continue with the installation from there, it won't let me. help.

---

### Post by skullmunky on 2010-12-27
hi new guy,

the term "FIXME" in that instruction means that whoever wrote that instructions left a note for themselves that they were supposed to go back and add an image.  

What it really means to say is that the mount point should be "/".  the character "/" is used in directory paths: for example, /home/skullmunky is where my home directory is.  a "/" by itself just means the root of the whole file system, which is what you want.  

The other partition you're creating is a swap partition, which is used for virtual memory.  Just set the type to "swap", you shouldn't have to set a mount point for it.  

I don't think it matters which partition is swap and which is ext4, but out of habit I've always out swap last.  

I usually prefer to do all the partitioning using GParted rather than using the Ubuntu installer - I find it's a little easier to tell what's going on.

---

### Post by gaboguy7 on 2010-12-27
thanks for the help and advice man!! I really appreciate it :D

---

