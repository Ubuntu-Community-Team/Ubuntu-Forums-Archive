---
title: "Error: &quot;Can't have overlapping partition&quot;"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by dodle on 2009-02-17
I can't figure out why it's saying this.  If I let the machine partition it automatically, it stops partitioning at 33%.  If I do it manually, it says: "Error: Can't have overlapping partition".  I even put 1mb of space between partitions.  Can anyone help me with this?  I'm using an Imac G5.

---

### Post by mkvnmtr on 2009-02-17
I have at times had to leave from 3 to 7 Mb on both ends of a partition I was forming. Just try it again with a little more space and you will find how much you need. It is  probably something about partial blocks that I don't understand.

---

### Post by dodle on 2009-02-18
I'm still getting the same error.  Do you think it might have to do with the hard drive?  It isn't the original that was in the machine, the lady that gave it to me kept it.  The drive that's in it right now is a Western Digital 250gb.

Edit:  I actually get two errors.  The first one says:  "Partition map has no partition map entry".  Then the second one says that I can't have overlapping partitions.  I even tried it with 50mb between partitions.  Should I use Ext2 instead of Ext3?

---

### Post by mkvnmtr on 2009-02-18
Well that is a bigger question. What are you working on the disk in your mac or an external? Can you form a partition with disk utility on yoour Mac os or the Mac install disk? If mac will form the partition maybe you can come back to gparted to format it.

---

### Post by dodle on 2009-02-18
I'm using the internal hard drive.  I don't have the mac installation discs.  I wanted to try gparted, but I couldn't find one for ppc.  I guess that I'll put the hard drive in my pc and partition it with gparted.

---

### Post by mkvnmtr on 2009-02-18
I f you have a live disk for Ubuntu you should be able to use the partition editor. That is Gparted. 8.04 might be the easiest to boot. I take it there is no system on the computer or do you have Ubuntu on it. You know you can't work on the disk form the same disk. Thee disk has to be unmounted and you need to use a bootable disk. The only ones I have found have been Ubuntu disks and that is a large download for just Gparted. As it happens I have several disks from installing on my mac.

---

### Post by dodle on 2009-02-19
There is no system installed.  I didn't find a live cd for ppc.  The only one I found was in the alternate cd section.  Is there a live cd for mac?

Edit: NVM, I found the live cd.  I'll try that.

---

### Post by mkvnmtr on 2009-02-19
Look at the second thread on this page for the links to the powerpc downloads. On my I book the 8.04 is the easiest to boot. You will need to have enough ram. I think they say 34Mb to boot the live disk.

---

### Post by dodle on 2009-02-19
Thanks, I'm going to try the 8.04 live CD.  I'm downloading it right now.  I'll let you know what happens.

**Edit:** The live cd works, but I think there is a problem with the hard drive as gparted returns errors when trying to format.  I'm attempting to format it to ntfs with a Windows disc right now.

---

### Post by dodle on 2009-02-19
The hard drive formats fine with a Windows XP cd, but I can't get any Linux distro to format it.

---

### Post by cyberdork33 on 2009-02-19
> **dodle said:**
> I'm attempting to format it to ntfs with a Windows disc right now.
> **dodle said:**
> The hard drive formats fine with a Windows XP cd, but I can't get any Linux distro to format it.
wait, what? are you on a powerpc mac or an intel mac?

---

### Post by dodle on 2009-02-19
Power PC.  I was just testing it on a Windows PC to see if it would format.

---

