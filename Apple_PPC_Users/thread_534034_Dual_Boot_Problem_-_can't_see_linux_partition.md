---
title: "Dual Boot Problem - can't see linux partition"
date: 2007-08-24
forum: Apple PPC Users
---

### Post by natgab on 2007-08-24
OK, here is my problem:

I have 40GB HD that was split into 2 partions w/ DiskStudio (techtoolpro company).  My drive also has a 4GB eDrive, for defrag/recovery.  OSX 20GB / 13GB Linux / 4GB eDrive

DiskStudio had set 2nd partition as an HFS+ empty.   I tried to load Yellow Dog Linux on the linux partition but it stalled at the partition part of the installation.  

I rebooted and now I can see the 20GB OSX (works) and the 4GB eDrive.  But I can no longer see the 13GB partition I made for linux.  I cannot see it using DiskStudio either.  I CAN see it under disk utility, but I cannot do anything without wiping the whole drive :(

Any chance to save my OSX partition w/o having to re-install my apps, etc ?  This was the reason I bought DiskStudio, for non-destructive repartitioning.

BTW: I also posted this on the YDL forum.  I'm pretty sure you guys will respond sooner, and then I can put either YDL or Ubuntu.

TIA, sorry for the long post.

---

### Post by bernied on 2007-08-24
What does fdisk tell you?
```
sudo fdisk -l
```
Run this in a terminal from a ubuntu live-cd (or another linux live-cd, but you may need to leave off the 'sudo').

If the partition is absent in fdisk you can recreate it.
It may also be of the wrong type - the Id and System columns will tell you this.

---

### Post by stmiller on 2007-08-24
> **natgab said:**
> 
DiskStudio had set 2nd partition as an HFS+ empty.   I tried to load Yellow Dog Linux on the linux partition but it stalled at the partition part of the installation.  


This may be the problem. It's better to leave the partition for linux as unformatted free space. Linux won't install on an HFS+ partition anyway, I don't believe.

So you CAN boot into OS X okay?

This is a tricky situation, but in a Linux install CD during the install you can remove that HFS+ partition you made for Linux and have the installer make its own partition in that raw unformatted space. It will then leave the OS X side untouched. It's better to do this anyway for making a dual boot system.

Backup all important data just in case.

---

### Post by natgab on 2007-08-25
---bernied

YDL does not do live disc.  I will have to burn a new ubuntu 7.04 disc, I had previously tried 6.06 and could only do it as a text install.  Should I try with an alternate disc & recovery mode ?


---stmiller

My OSX partition is perfect & works.  But after rebooting from the stalled installation, I cannot see the partion I had made for YDL.  I also still see my 4GB TechToolPro eDrive.

DiskStuido give me the following choices:  HFS+ journaled/non-journaled, HFS+ case sensitive/non-case sensitive and UFS.  It does not give the choice of free space.  

I sent an email to to Micromat to ask if TTP 4 / DiskStudio can do anything to recover my partition.  I will hold off on doing anything untill I receive an email from  them.  

I'm trying to preserve OSX partition since I have several apps installed and all set to my liking.  My data is back-upped.

Any other ideas gladly accepted, It will just be a few days before I can try them.  TIA

---

### Post by bernied on 2007-08-25
[EDIT: my apologies, I am very much out of my depth here, I hadn't noticed I was in the PPC forum. Try anything I say with caution]

I realise that I might be a little out of my depth here, because I have no experience with OSX. I have some vague notion that OSX uses a different disk layout compared to linux and MSDOS/windows. I also have no knowledge of these disk/partition utilities of which you speak.

Still, if a linux live-cd will boot, and it can see the partition (meaning it has an entry in /dev), then you can put whatever filesystem you like on it. But I suspect that there is something wrong with your partition table if your utilities cannot see the partition. Which means you need something like fdisk, which you should find on any linux live-cd. But I'm not sure whether fdisk can handle disk layouts other than the one linux uses.

So I guess my original question is still valid - what does fdisk tell you? If it gives you lots of crazy messages about not being able to read the partition table, or the partition table being invalid, then be very very careful. Don't write any changes to the partition table until you are confident. You might even consider taking a copy of the master boot record (mbr), which includes the partition table, like they do at the bottom of [this page](http://www.debianhelp.co.uk/ddcommand.htm).

If downloading is not quick for you, try a small live-cd. Slax is my favourite - it's about 100MB, and it certainly has fdisk on it - in fact I'm pretty sure it has cfdisk, which is a little easier to use.

---

### Post by Auria on 2007-08-25
> **bernied said:**
> 
If downloading is not quick for you, try a small live-cd. Slax is my favourite - it's about 100MB, and it certainly has fdisk on it - in fact I'm pretty sure it has cfdisk, which is a little easier to use.

Careful, this is the PPC forum :) I don't think Slax has a PPC version

---

### Post by bernied on 2007-08-26
> **Auria said:**
> Careful, this is the PPC forum :) I don't think Slax has a PPC version
Ah, yes. I am so sorry, I should not even be here. It's my old eyes, they're not what they once were.

---

### Post by natgab on 2007-08-28
OK

I tried using TechToolPro 4, but it wouldn't show linux partition.    DiskStudio tech support said to use Disk Utility.  While booted from TTP, I tried Disk Utility.  It showed partition, but did not let me access the partition.

Solution:

I booted off Kubuntu 6.06 disc I burned.  I ran install, this did see the partition.  I first set the 13GB partition as empty space.  Then I simply told installer to use largest contiguous space as a linux partition for Kubuntu. While keeping my OSX partion :)

Unfortunately, it ran almost the entire install but chocked toward the end when installing software.  I then tried the YDL 5 DVD, it installed perfectly.  But I do not have internet yet.  I will see if I can get it to work.

Does anybody know if (K)ubuntu 7.04 installs ok on a Clamshell 466 SE ?  Do you get wireless ?

---

