---
title: "[SOLVED] I killed Ubuntu with a home partition"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by wallywally on 2007-11-01
Having deleted my Windows partition I have tried to create a separate home partition in Ubuntu by following the instructions here: [www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

However upon rebooting my machine all hell broke loose; booting Ubuntu on the hard disk only works using the Failsafe Terminal; booting Ubuntu Recovery Mode on the hard disk takes me to root@ wallywally-desktop:~# [fail]; starting or installing Ubuntu from Live CD shows me the Ubuntu logo and moving orange bar then flashes an orange screen for a second before going blank.

Only starting Ubuntu in safe graphics mode from Live CD works – which is where I am now.

In Computer I can see the following.

CD-RW/DVD+-RW Drive
34.0 GB Volume: disk
39.1 GB Volume: disk-1
Filesystem

The 34.0 GB Volume is my Ubuntu partition which now contains a folder called 'home_backup' and a folder called 'home' which also contains a folder called 'home_backup'. 

The 39.1 GB Volume is was formerly my XP partition which I killed using Gparted. It has the same contents as the 'home_backup' folder.

I have tried fixing things (following the instructions at the end of the psychocats tutorial) via the terminal in Failsafe Terminal mode but what that has done I do not know - it hasn't fixed it.

Using the terminal in safe graphics mode from Live CD I have typed “sudo fdisk -l” which gave the following result:

Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xfa38fa38



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        5099    40957686   83  Linux

/dev/sda2            5100        9533    35616105   83  Linux

/dev/sda3            9534        9729     1574370    5  Extended

/dev/sda5            9534        9729     1574338+  82  Linux swap / Solaris


sda1 was where windows used to live and where I want home to be when (if I ever) I get things working again.

I thought perhaps that I should fiddle with fstab a bit more but when I type “sudo nano /old/etc/fstab” into terminal I get taken to File: /old/etc/fstab which is a blank page.

I now don't have any idea how to set about either achieving my original goal of a separate home partition or, failing that, restoring things back to the way they was.  If anyone has any suggestions I should be most grateful if they could be kept as simple as possible since, as has been probably made clear by reading the above, I am an idiot.

---

### Post by HermanAB on 2007-11-01
Copy your data off and re-install.  This time, make a /home partition during the disk drive configuration, don't just accept the defaults.

---

### Post by Partyboi2 on 2007-11-01
When I tried the same link you used to make another /home I had problems as well, ended up having to reinstall.

---

### Post by alienexplorers on 2007-11-01
Just reload Ubuntu and set it up with a / and /home directories.

---

### Post by wallywally on 2007-11-01
Cheers for the advice people – I've reinstalled Ubuntu and set it up with sda1 as /home and sda2 as /

All of my data is still there and everything is ticketyboo.

However, when I look in Computer there is only one disk called Filesystem which is 33.4 GB and so is presumably sda2.  Should I be able to see sda1 as well?  

Filesystem contains a Home folder with all my stuff in it which I was surprised to see as I thought Home would be sda1.

How can I check that the partitions are operating as intended?

---

### Post by MaximusTG on 2007-11-01
Well, that's one of the beauty's of linux, and all *NIX's, the filesystem is totally transparant. In your / filesystem, you have mounted the /dev/sda1 partition at /home. So, the "folder" home is actually your /dev/sda1 partition. 
You could check this, both partitions are +- 30 GB's right? When you open nautilus, and go the root of your filesystem, you see the amount of free space. Probably around 20 GB's free right? Now, when you view the properties  of /home, it has probably more free space (or less depending on the amount of data you have.. ) than the root filesystem!

---

### Post by wallywally on 2007-11-01
Excellent!  Many thanks Maximus.  It is exactly as you say it should be.

---

