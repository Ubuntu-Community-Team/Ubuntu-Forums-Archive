---
title: "3 Issues Before I Start"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by ityro on 2006-09-05
I am new to Ubuntu/Linux. All I have done so far is read some of what is available on the Ubuntu sites which is impressive, but most is over my head just as it was with Windows 2.5 years ago.

I have been using XP Pro on a HP/Compaq nx9010 notebook with a HP Deskjet 5740 printer, a HP Scanjet 3770 flatbed scanner and an Iomega removable 80mb HDD (two partitions).  The system is for home use only and I am the only user.

I have three issues to settle before I start:

1.  Using the Guided Partitioning Option in the Graphical Install procedures from the Community, more than one partition is created. Does this mean the system will be in a different partition from my data?

2.  I would like to know how to remove/uninstall Ubuntu before I install it. I "searched" but did not find procedures for removal just the promise
that uninstall was available. If I don't get it right the first time I want to uninstall and reinstall until I do get it right. So, how do I uninstall Ubuntu?

3.  When I uninstall Ubuntu, will it do a complete removal and put things back the way the were?  (e.g. the C: drive will not be partitioned)

Thanks for your time!

---

### Post by Crayoneater on 2006-09-05
1. it is probably making a root partition and a swap partition...the operating system will be installed in the root parition and the swap is just used for storing unused memory items until they are needed...so it will have no files in it...

2. to remove ubuntu, you can just reformat the partition(s) that it is installed on

3. i'm kind of confused...are you talking about dual booting ubuntu and windows? if you are wanting to install ubuntu along side of windows, you need to make sure you know what you are doing if you are worried about losing any data on your windows drive....i guess if you have created seperate partitions for ubuntu, then you should be fine, as long as you remember which partition is your windows partition and leave it alone....also, back to question 1, it is probably giving you a root partition, swap partition, and showing you where it will mount your windows partition, assuming that you are, in fact, trying to dual boot....

hope this helps....

---

### Post by bodhi.zazen on 2006-09-05
> 1. Using the Guided Partitioning Option in the Graphical Install procedures from the Community, more than one partition is created. Does this mean the system will be in a different partition from my data?
No, it is as Crayoneater described. The swap partition is used by the system as you run applications. Windows does the same thing, I forget what Microsoft calls it, but windows does not use a separate partition.

> 2. I would like to know how to remove/uninstall Ubuntu before I install it. I "searched" but did not find procedures for removal just the promise
that uninstall was available. If I don't get it right the first time I want to uninstall and reinstall until I do get it right. So, how do I uninstall Ubuntu?
Crayoneater is partially correct. You will likely have to restore your MBR (master boot record) or you will not be able to boot windows after you re-format your Ubuntu partitions. Thus it is a two step process:

1. Reformat your Ubuntu partition.
2. Restore your MBR (windows boot).

> 3. When I uninstall Ubuntu, will it do a complete removal and put things back the way the were? (e.g. the C: drive will not be partitioned)
Yes you can do this. Just follow the above steps and finally use the same partitioner you used when you installed Ubuntu and reverse the process.

---

### Post by ityro on 2006-09-05
Crayoneater, 

My sincere thanks for your response to my post. 

So installation of Ubuntu, like Windows, puts your data in the same partition as the system when using the default installation.  Good to know.

My fault for causing confusion!  Yes, I am looking at a dual boot system. I thought of reformatting, but knowing I was to use a dual boot system I did not like the idea of leaving the partitioning behind.

I could use Windows Automated System Recovery along with the ntbackup option of "backup everything on this computer". That would put everything back the way it was and avoid a Clean Start (if all goes well). 

Thanks again and sorry for the confusion . . .

---

### Post by ityro on 2006-09-05
I did not know how the forum works! Thanks to all involved. I will print the new information,

Thanks Again.

---

### Post by ityro on 2006-09-06
Here comes a dumb question: Can I install Ubuntu on my removable Iomega HDD which is USB? I have two partitions, E: and F: which are 40GB each. I could use F: for Ubuntu. If not how about running "Live" from the Iomega? (copy download from C: to F:)   I had to ask.

---

### Post by bodhi.zazen on 2006-09-06
> **ityro said:**
> Here comes a dumb question: Can I install Ubuntu on my removable Iomega HDD which is USB? I have two partitions, E: and F: which are 40GB each. I could use F: for Ubuntu. If not how about running "Live" from the Iomega? (copy download from C: to F:)   I had to ask.

Yes. to installing to Iomega. This drive will be /dev/sda rather then dev/hdb.

Not easily re "live" from Iomega.

---

### Post by ityro on 2006-09-06
Thank You bodhi.zazen,

Let's see if I can do it without anymore help.

Thanks Again ...

---

