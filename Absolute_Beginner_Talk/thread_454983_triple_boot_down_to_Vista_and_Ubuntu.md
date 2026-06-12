---
title: "triple boot down to Vista and Ubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-26
Ok guys here is the situation. Right now I am triple booting between XP Pro, Vista and Ubuntu. XP is my primary (C:\) and ubuntu, vista and a data partition all exist. I had a problem tonight with a corrupt conf file in XP. Because of this, I have lost Grub and can not get into Ubuntu. I can access Vista still and all the files stored in my C drive, data partition and Vista. I want to get rid of XP Pro, and have Vista and Ubuntu in a dual boot configuration, with my data partition as well to be accessed by both (will mount in ubuntu). Partitions should look like 
Vista (C) 40GB
Ubuntu (U) 40 GB
Swap File 2GB
Data (F) The rest of the hard drive (using a 320 GB Seagate)

Right now they look like this:
C: XP 20GB
Data 190 something GB (I think)
Swap 2GB
Ubuntu 60 something GB
Vista 20GB

So my questions are:
1. How do I restore Grub? I know there are plenty of posts but its late and I will search tomorrow - can u just point me in the right direction or give me a how to.
2. How do I get rid of XP and move vista from the partition it is on to the main partition? I am ok with formatting vista as I do not have much installed or configured yet.
3. Is it possible to leave ubuntu alone while doing all of this? Right now it is 60GB in size but I plan to use the live cd to resize Ubuntu and allocate the free space (Hopefully, not sure how to allocate to the data partition)
4. How would you recommend setting up Ubuntu if it needs to be reinstalled during this process?

Sorry for all of the questions.

---

### Post by krisfrajer on 2007-05-26
Hi
When your grub was working property, vista was in your grub menu as one of your options for rebooting?

---

### Post by jba6511 on 2007-05-26
yeah it was generic kernel
kernel recovery or something
memtest 86+ 
Ther operating Systems:
Vista/Longhorn loader

and then I would choose the vista loader and it would bring up vista's loader to choose between xp and vista.

---

### Post by jba6511 on 2007-05-26
ok I went ahead and used gnome partition from the livecd to remove xp and vista, and then I installed Vista on the C: drive.
My partitions now looks like this:

c:\ 20GB Vista
d:\ 192 GB Data
2.73 GB Linux Swap
63.35 GB Ubuntu
20GB Unallocated

This is closer to what I want. Now I need to get Grub to boot at startup to allow me to switch between Vista and Ubuntu. I found a thread here;
[http://ubuntuforums.org/showthread.php?t=24113&highlight=GRUB+Windows](http://ubuntuforums.org/showthread.php?t=24113&highlight=GRUB+Windows)
 But when I reach the step where it says to mount your linux partitions, I get lost. I installed Ubuntu by selecting the largest continous free space option and do not know how to mount my appropriate linux partitions. Therefore, what should I do in this step?

---

### Post by jba6511 on 2007-05-26
Well I tried the method listed in this page here: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) and was able to get to the grub loader menu, but then when I selected kernal ... I got an error 22 that the partition does not exist or something along those lines. Any ideas guys?

---

### Post by jba6511 on 2007-05-26
reinstalled ubuntu - did not have that much on it anyways as I had just installed it.

---

