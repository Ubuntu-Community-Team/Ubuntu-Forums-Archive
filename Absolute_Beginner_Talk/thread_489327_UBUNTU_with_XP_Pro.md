---
title: "UBUNTU with XP Pro"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by leeorc on 2007-07-01
Hi,
I have install Ubuntu 7.04 on a Comuter that Win XP Pro already installed.

I did manual definition on the Hard Drive(third check box on live cd install tool), 
I created  Partition for SWAP(500MB),
and one for the system Root File(2100MB)...
After the installation ended I made boot and Windows XP is loaded automatically,
How can I boot my UBUBTU without the livecd (from the hard disk), after I Installed it??

TNX

Leeor

---

### Post by AlexenderReez on 2007-07-01
> **leeorc said:**
> Hi,
I have install Ubuntu 7.04 on a Comuter that Win XP Pro already installed.

I did manual definition on the Hard Drive(third check box on live cd install tool), 
I created  Partition for SWAP(500MB),
and one for the system Root File(2100MB)...
After the installation ended I made boot and Windows XP is loaded automatically,
How can I boot my UBUBTU without the livecd (from the hard disk), after I Installed it??

TNX

Leeor

root file system is only 2100mb....i wonder why you spend so small space for ubuntu...even if for testing....i think there could be something wrong with installation....are you really confirm that you installation is not failed?

---

### Post by oilchangeguy on 2007-07-01
this is a quote from the ubuntu website - System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 4 GB of disk space. 


i'd suggest making your partition larger. i'm sure the os did not completely install.

---

### Post by leeorc on 2007-07-01
Should my choice (Manual Partition) should load the UBUNTU from a dual booting choice??

---

### Post by leeorc on 2007-07-01
Oilchangeguy ,
 Should I destinate 4GB for the File System Root? ???

TNX

---

### Post by oilchangeguy on 2007-07-01
> **leeorc said:**
> Oilchangeguy ,
 Should I destinate 4GB for the File System Root? ???

TNX

i'd suggest a 10-20gb partition. and let ubuntu set it up how it wants to.

---

### Post by AlexenderReez on 2007-07-01
what is your problem with 4g of space...this is operating system ....not a software....i used to wasted about 8gb for fresh install vista ultimate(not including other software!)  and yet i use 30 gb for ubuntu as i'm more on ubuntu...vista is just for testing software....and gaming.....the point is...that is requirement....just follow if you want to install......

---

### Post by Dedoimedo on 2007-07-01
Hello,
Do you see the GRUB menu at all? Or does XP load as before?
Dedoimedo

---

### Post by leeorc on 2007-07-01
XP Loads before and I dont see grun menu
And should I use 4 GB for the File System Root ???
Cause I gave it only 2 GB as recomended in installation wizard...

---

### Post by dptxp on 2007-07-01
> **leeorc said:**
> XP Loads before and I dont see grun menu
And should I use 4 GB for the File System Root ???
Cause I gave it only 2 GB as recomended in installation wizard...

4 GB is OK for / if you store data in a separate partition as /home or any other.
Make SWAP of 1 to 2 GB.

Are you really short of disk space ? 4 GB is minimum for 7.04.

---

### Post by Dedoimedo on 2007-07-01
Hello,
I would warmly recommend you reinstall, with proper partition sizes. It can be that some packages were not installed. Most likely, you have not installed the bootloader either, or maybe overwritten it.
You might also want to separate /home from / on a different partition.
Dedoimedo

---

### Post by leeorc on 2007-07-01
I dont know y people judged me...
I have enough space... and not only 2GB
but I installed as recomended for the File System Root 2 gb,
And the system let me install...
SO my question is:
1. Should I Reconfigure and  install again the "File System Root " cause I gave it only 2gb in installation(as recomended in Installation wizard of live-cd).
2. Is " "File System Root"('/' ) Considered as the whole operating system except the SWAP..(I did onky 2 new partitions ).
3. Is it possible that the installtion wizard do not install GRUB on the manual radio button selection ???

please be relevant

TNX

---

### Post by dptxp on 2007-07-01
> **leeorc said:**
> I dont know y people judged me...
I have enough space... and not only 2GB
but I installed as recomended for the File System Root 2 gb,
And the system let me install...
SO my question is:
1. Should I Reconfigure and  install again the "File System Root " cause I gave it only 2gb in installation(as recomended in Installation wizard of live-cd).
2. Is " "File System Root"('/' ) Considered as the whole operating system except the SWAP..(I did onky 2 new partitions ).
3. Is it possible that the installtion wizard do not install GRUB on the manual radio button selection ???

please be relevant

TNX

OS resides in root.
You will add many programs too. They will go to root. And you do not have any space left.

---

### Post by BHelts on 2007-07-01
nobody's judging you.  the ubuntu site states that:

> System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 4 GB of disk space. 

where did you get the information that only 2GB were needed?

---

### Post by leeorc on 2007-07-01
Sorry Dedoimedo ,
But I am not familiar with the /home purposes,
For what do I need to seperate it? 

Isnt it enough to mount Root system '/' and swap ? 

Leeor

---

### Post by oilchangeguy on 2007-07-01
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
you're making something that's really easy. really hard.

---

