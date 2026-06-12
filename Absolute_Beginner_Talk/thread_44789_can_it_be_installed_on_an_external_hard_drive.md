---
title: "can it be installed on an external hard drive?"
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by stu2004 on 2005-06-27
can ubuntu be installed onto an external hard drive leaving my main drive alone?
if so how?

secondly, if you install it onto your main drive (e.g c:/) how easy is it to remove it?

thanks,

stu

---

### Post by apollo2011 on 2005-06-27
I am not sure whether or not you can install it on an external drive, you might run the install until you get to the Partitioner and see if the external drive shows up or not.

However, I can answer your second question.  Ubuntu is much easier to get uninstalled then installed.  You just wipe out the partition.  The hard part is partitioning your disk so that you can put Ubuntu on it.

Although, now that I think of it, I am not sure how the bootloader will react if you just wipe out the partition.  Someone else will have to answer that more fully...

Hope that helps some.

---

### Post by b_martinez on 2005-06-27
[QUOTE=stu2004]can ubuntu be installed onto an external hard drive leaving my main drive alone?
if so how?

secondly, if you install it onto your main drive (e.g c:/) how easy is it to remove it?

thanks,

stu[/QUOTE]
 I just (re-) installed Ubuntu. The partitioner saw my USB hard drive, so it SHOULD see yours (no promises). My advice would be for you to attempt to install Ubuntu to the sda (external) drive, and put the boot loader onto a floppy disc (fd0 [that is a zero ,not the letter]). This will keep your original system intact, bootloader and all. 
 I do not recall seeing a way to resize the partition, so it may just wipe the file system on your external hard drive. Someone with experience can answer that question.  Read the installation notes/manual to find out how to do the re-size. There are third party  partition managers, but, from what I've read, they pretty much lock the system into whatever you initially partition. Meaning that you will have to do a LOT of stuff to re- size if you decide to give more space to Ubuntu.
Good Luck with this.
Bill

---

### Post by Quizbiz on 2005-11-25
I would like to install ubuntu on to my external drive, I just don't know how.

---

### Post by tomwell on 2005-11-25
[QUOTE=apollo2011]
Although, now that I think of it, I am not sure how the bootloader will react if you just wipe out the partition.  Someone else will have to answer that more fully...
[/QUOTE]

If you just wipe The partition GRUB (the boot loader) Will still load and you will get an error message but its ok... just reinsert a windows CD and you can reeinstall the windows boot loader...

There are a few threads about it in more detail...

Peace

Ps: It should be possible to install Ubuntu on a external drive, I have read about someone that has managed to load it onto a 4gb drive... not sure how to but a search in the forums will yield results for sure...!!



Tom

---

