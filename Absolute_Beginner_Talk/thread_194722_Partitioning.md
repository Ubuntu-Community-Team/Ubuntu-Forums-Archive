---
title: "Partitioning"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Binh on 2006-06-11
Okay, so partitioning is splitting a hard drive in pieces, sort of. Can this be undone? If I decide to go dual boot for a while (BTW, the dual booter, grub right? it comes on the installation cd, correct?), and then all of a sudden switch completely back to windows (OMG, lol) can I piece my hard drive back togeather into one complete :C drive? Lastly, if I want to share files between linux and XP, I need to make a third partition, right? Does the Live CD do that?

---

### Post by glotz on 2006-06-11
Yes. (Windows' the one you'll be dumping...) Yes. (FAT32 format) Oh yes.

---

### Post by Engnome on 2006-06-11
[QUOTE=Binh]Can this be undone? [/QUOTE]
Yes, remove partition you dont want and resize the one you want to keep to fill the entire hdd.

[QUOTE=Binh]can I piece my hard drive back togeather into one complete :C drive?[/QUOTE]

You can use the windows cd to restore the original boot loader. Not really necessary. Just tell grub to boot windows automatically.

[QUOTE=Binh]Lastly, if I want to share files between linux and XP, I need to make a third partition, right? Does the Live CD do that?[/QUOTE]

Setting up a mutual fat partition is a good idea. The text mode installer can do this, not sure about live (never used it)

---

### Post by hanexar on 2006-06-11
> 
Originally Posted by **Binh**
Lastly, if I want to share files between linux and XP, I need to make a third partition, right? Does the Live CD do that?

Fat32 is what I use to share between windows and ubuntu. I made it before installing ubuntu from within windows, with the partitionning tool (I don't quite all the detail to do this, it's been a few years already), but it was quite easy to do.  Just browse through your windows tools.

---

### Post by catlett on 2006-06-11
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) This is my favorite partitioner. It runs off a live cd. Which is nice because your drive remains unmounted and you can perform changes in real time.
This can make partitions and then later on delete partitions. If you were to remove partitions, you would choose the linux partitions and select "delete". You would then choose your windows partiton and select "resize". This will let you make the windows partition the size of the entire drive again.
If you get rid of the linux drives then grub will be erased as well and you will not be able to boot to windows. If you delete linux then put in a windows install disk (or your factory recovery disk) and choose "recovery mode". It will take you to a comand prompt. At the prompt enter "fixmbr" (without the quotes, of course).

You can get technical but you only need to have one 10gb partitionb for Ubuntu. If you make it before hand with gparted, just choose that partition and select to automatically partition it. Ubuntu will make a small swap partition and keep the rest together as an ext3 partition. The entire installation will then be put on that partition. 
To remove linux just use gparted to delete the 2 partitions created at install and then resize windows back to it's original size. Put in the windows install disc, run it in recovery mode, enter fixmbr at the prompt and your back to being a  drone in a Gatesian world. (only kidding you will be back to windows)

---

### Post by user1397 on 2006-06-11
oops completely off-topic :)

---

