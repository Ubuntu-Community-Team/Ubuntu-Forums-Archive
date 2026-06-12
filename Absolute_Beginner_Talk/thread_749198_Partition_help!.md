---
title: "Partition help!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by krizmo on 2008-04-08
Hello everyone, as you may be able to see I am new here, and new to Linux.

Actually, I still haven't got ubuntu working atm, I just can't seem to get my head around partitions. I mean, I understand what they are and stuff, but I cannot find _anything_ that provides a simple explanation on how to partition a HDD. I am really stuck...

So, what I ask of you is this:
Can someone please tell me how to do this, step-by-step would be excellent, a link to somewhere that has this information would be nice.
Oh, and for what I want to do... I currently have a 20GB HDD (18.9) with Windows XP installed. I have 6GB of free space. I guess I should ask, is this enough? What I want to do is partition the HDD so that I can have a dual-boot going on, to test out ubuntu before I buy my new PC (I am too poor to afford Windows T_T).

Oh, and another thing, I have no CD drive... which makes things a whole lot more... crap.

Anyway, I hope someone out there can help me, and I hope this isn't too long a post. ANd go easy on me, I know a little about windows, but I've only started learning about the hardware aspect of things...

THANKS IN ADVANCE!

And sorry if I have missed anything! Just ask, and I'll be sure to give you any info you need!

EDIT: I forgot to add;
Because I have no CD drive, I had to try and boot the OS from a USB flash drive using this tutorial -> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) . When I booted from the USB drive, it came up with the error of 'invalid partition table' and went no further. This is the reason I tried to find out about partitioning, and any help regarding this would be much appreciated

---

### Post by The Cog on 2008-04-08
By having 6G free space, I assume this means free space inside your windows partition. It's no use for making partitions from while it's there. You will need to reduce the size of your NTFS windows partition. Theoretically, you could reduce it by 6G, but fragmentation may mean it cannot in practice be reduced that much. Before you start installing, do several defrag runs and make a backup that you know you will be able to restore from if needed.

The Ubuntu installer can reduce the size of the windows partition. Ideally you want to free at least 4G. After this, the installer can use the space created to make the partitions it needs for Ubuntu. 

I believe you can get the Ubuntu installer bootable on a pen drive, but you will have to google for a howto.

---

### Post by krizmo on 2008-04-08
Yes, I mean in my Windows partition.

I also have a problem with defrag-ing... whenever I open up the windows defrag utility it says "MMC requires Internet Explorer 5.5 or greater to be installed.", even though I have IE7 installed... any insight on this?

And also, by a backup do you mean my whole HDD backed up onto a seperate source?

And do you also mean that I should just get the ubuntu installer to make the partitions for me, if and when I get it to work?

btw, thank you for the quick reply!

---

### Post by aeiah on 2008-04-08
you should have a look into wubi. you should easily be able to install ubuntu from inside windows and create a dual boot setup. ive never used it but its ideal for beginners, and especially so since you dont have a cd drive. when you have your new pc you'll probably want to install ubuntu normally though

---

### Post by aeiah on 2008-04-08
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by louieb on 2008-04-08
> **krizmo said:**
> ... I currently have a 20GB HDD (18.9) with Windows XP installed. I have 6GB of free space. I guess I should ask, is this enough?

Its enough for Ubuntu,  but windows will really suffer.  NTFS (widows XP file system)  needs some free space. Ideally you want it to stay under 70% full. Once it gets fuller that that it has a hard time with fragmented files and performance drops.

---

### Post by hyper_ch on 2008-04-08
and if you decide to partition anway, make backups first. Resizing partitions can render your harddisk useless and then you'll have to format it all.

---

### Post by The Cog on 2008-04-08
> And also, by a backup do you mean my whole HDD backed up onto a seperate source?
Absolutely. Either an image, or a copy of all your contents plus a windows installer disk. Losing our entire disk contents is unlikely but it happens. It happened to me once, but in my case it was just the partition table that got screwed so I restored it from a backup image. Repartitioning always carries a small risk of total data loss. And that's regardless of why or how you repartition. Inexperience (or over-confidence) multiplies the risks.

You should have a backup anyway - hard disk failures and laptop thefts often happen without warning.

---

### Post by krizmo on 2008-04-08
Hey thanks a lot aeiah, I'm checking out wubi as we speak, and all seems good.

And thank you to everyone else who has helped out here, it is much appreciated. If I have any more problems, you'll be sure to hear from me!

---

