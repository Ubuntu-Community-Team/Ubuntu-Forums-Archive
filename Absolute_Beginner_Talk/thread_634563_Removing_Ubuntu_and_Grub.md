---
title: "Removing Ubuntu and Grub"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Ozwego on 2007-12-07
Hey I want to remove ubuntu and grub from my machine.

I have two hd's, ubuntu is on my slave.  Anyone able to point me in the right direction as to not get the dreaded error 21 after I reformat my slave drive?

---

### Post by Duck2006 on 2007-12-07
This should help.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by CaptainInsaneO on 2007-12-07
If you have a windows disc, all you need to do is boot into windows, format your Ubuntu disk, and then boot with your windows disk and run fixmbr. If you don't have a windows disk, follow duck's advice.

---

### Post by louieb on 2007-12-07
more ways to do just that: [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by rsambuca on 2007-12-07
Just install ms-sys from synaptic or 'sudo apt-get install ms-sys'.  You can then just use it to remove grub and put a Windows loader back to the mbr.  You can then boot into Windows and delete the ubuntu partition.

---

### Post by hydraconsole on 2007-12-07
After i reformatted the ubuntu partition, can i use the ubuntu livecd to add that partition to my existing winxp partition without affecting the data on my winxp partition? What do i do so that i don't loss any data. thanks

---

### Post by rsambuca on 2007-12-07
> **hydraconsole said:**
> After i reformatted the ubuntu partition, can i use the ubuntu livecd to add that partition to my existing winxp partition without affecting the data on my winxp partition? What do i do so that i don't loss any data. thanks

First, BACKUP ALL OF YOUR DATA.  There is always a risk of data loss when using partitioning.  In fact, drives have a 8% failure rate per year, so you should back up always anyways.

Second, in theory, yes.

---

