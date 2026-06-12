---
title: "Format and name partitions"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-11-19
I have a 2 Gb USB flash drive that I used gparted to divide into 4 primary partitions of about 500 Mb each, and format as FAT32. Seems to work fine as long as I'm using Ubuntu 7.04 (nautilus) on my desktop or Xubuntu 7.10 (thunar) on my laptop. In either case, I appear to have 4 drives whenever the flash drive is plugged in. When I do plug in, all four mount at the same time, and to unmount, I just use nautilus to unmount, and they all unmount at once. That's OK, as far as I'm concerned.

But when I dual-boot my desktop into Windows XP, I can only see one of the partitions. What gives?

Another question, probably related: In Windows, you can name or rename a drive. (I don't think this is the same as "label," which I understand actually controls the partition size and format.)  I did that for the one partition I can see from Windows, and it's "sticky;" that is, in Ubuntu or Xubuntu that partition shows up with that name. So how do you "name" a drive in Ubuntu or Xubuntu? (If I could see the other three partitions while in Windows, I'd just do it from there.)

---

### Post by question_chick on 2007-11-19
it could be that in windows they are all trying to mount on the same letter.

Right click on my compuyer and select manage

go into disk management

you should see all 4 partitions in there

give each a different drive letter.

---

### Post by dwiedenfeld on 2007-11-19
> **question_chick said:**
> it could be that in windows they are all trying to mount on the same letter.

Right click on my compuyer and select manage

go into disk management

you should see all 4 partitions in there

give each a different drive letter.

That doesn't seem to work. I can find nowhere in Windows that it's able to "see" the other three partitions. 

It also just occurred to me that there is a hidden partition on the hard drive that Windows XP boots from. It's one of those hidden partitions that Dell put on the machine to help you "recover" or "reinstall" from. Windows can't see that partition, either, but **nautilus can** (via NTFS-3g). I wonder if this is the same thing? That is, are the three partitions on the flash drive somehow "hidden" from Windows?

---

### Post by dwiedenfeld on 2007-11-19
Another bit of information: the 4 partitions show in gparted as their mount points:

/dev/sdc1 (this is the only one seen by Windows)

/dev/sdc2

/dev/sdc3

/dev/sdc4

---

### Post by dwiedenfeld on 2007-11-20
Bump. 
Any ideas?

---

### Post by natehatewindows on 2007-11-20
so if you do the manage thing from widows you only see one partition?

start button>>

right-clcik on computer>>manage

then click the disks (or something like that) on the left when the windows management window comes up.

---

### Post by dwiedenfeld on 2007-11-20
Yes, I see only one partition, the one that in gparted is named /dev/sdc1.

---

### Post by louieb on 2007-11-20
What filesystem are you using on the 3 unseen partitions?

---

### Post by natehatewindows on 2007-11-20
wow....thats really strange. i have no idea....sorry :(     even if they are ext3 windows should see them.

---

### Post by natehatewindows on 2007-11-20
louieb...great quote....i have never seen that one :)

---

### Post by philinux on 2007-11-20
As far as I know windows cannot see ext3 formatted drives or partitions.

Maybe the OP would be better to format the whole usb drive as vfat.

---

### Post by natehatewindows on 2007-11-20
when i had vista it saw all of my ext3 partitons with the managment tool.

---

### Post by louieb on 2007-11-20
if their  ext3 the windows file manager won't see them. 
Computer>manage> Disk management will see them but won't know what they are.
You can use one of these.
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")

[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")

---

### Post by dwiedenfeld on 2007-11-20
> **louieb said:**
> What filesystem are you using on the 3 unseen partitions?

They're all 4 FAT32.

I suspect they must be hidden. But how did that happen, and how do I undo it?

---

### Post by dwiedenfeld on 2007-11-20
Here's another question.

In gparted, some of the partitions on my computer have padlock icons next to the partition name, but others don't. 

(In the case of the four partitions in question on the flash drive, all 4 have the padlock symbol. But on the partitions on my hard drives, some have it and some don't.)

I can't find any information on what these icon symbols mean, or how they got there or how to get rid of them.

---

### Post by dwiedenfeld on 2007-11-20
> **dwiedenfeld said:**
> Here's another question.

In gparted, some of the partitions on my computer have padlock icons next to the partition name, but others don't. 

I can't find any information on what these icon symbols mean, or how they got there or how to get rid of them.

Any idea what these padlock icons mean, anyone?

---

### Post by dwiedenfeld on 2007-11-20
Well, I guess I have more information, and the news isn't good. It looks like **you can't EVER format a flash drive so that Windows XP will recognize more than one partition**. Some people seem to recommend Partition Magic and so forth, but the people who try it always come back to the same problem: you can't format a flash drive so that Windows XP will recognize more than one partition. 

Here's a good example of what I found:
[http://www.techspot.com/vb/topic18736.html]("http://www.techspot.com/vb/topic18736.html")

So, basically, what I'm trying to do has failed:(; can't be done for Win XP.

But Linux **CAN** do it. 

Yet another way Linux is superior to Windows trash.

---

