---
title: "How to allocate a partition to the /home directory?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-06-05
Please help me:

I have Ubuntu 7.04, and I also have windows XP in an ibm laptop of 60 GB  of HD. When I first installed ubuntu i left 29.5 GB for XP (i.e. for dev/sda1/) and 20.6 GB for ubuntu (i.e. /dev/sda3).  Later, I reduced the size of the "windows" partition to 13.73 GB using the GParted software, which produced a new partition that is  unallocated of 15.73 GB. 
What I want to do?, is to allocate that memory space (15.73 GB) to Ubuntu, specifically to my home folder.
In pic1.png you can see what appears when i open GParted. When I type in the terminal "$ sudo fdisk -l" appear the following information
-------------------
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1792    14394208+   7  HPFS/NTFS
/dev/sda2            6697        7296     4808160   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            3846        6572    21904627+  83  Linux
/dev/sda4            6573        6696      996030    5  Extended
/dev/sda5            6573        6696      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order
-------------------

What I have done so far? I followed these instructions ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)), i.e. in GParted right-click at the unallocated partition, then click "new" but appear a windows (see pic2.png) saying that "is not possible to create more than 4 primary partitions". It says that i need to delete a primary partition first, but i am afraid what this could produce, and i am not sure how to do it.

Can somebody help me, PLEASE?

thanks in advance

---

### Post by Clay_Banger on 2007-06-05
you cannot have more then 4 primary partitions, pretty much what the error message says. You need to convert one of the primary partitions into a logical one, then create all of your other partitions within this logical partition.

As you already have a logical partition where swap is, I will go through moving your partitions around to get that extra partition for /home. Warning! This will take a while.

Move /dev/sda3 across to as far left as it will go.
[IMG]http://img245.imageshack.us/img245/1090/move1oa4.png[/IMG]
Then increase the extended partition to fill up all of the space in the middle. -not sure how you would do this, but it will need to look something like this:
[IMG]http://img155.imageshack.us/img155/5207/increasewb7.png[/IMG]
Then just create a partition in the unallocated space and use the rest of the tutorial you were following to achieve your separate /home

---

### Post by cseljatib on 2007-06-05
hi there
some questions following your recomendations
>Move /dev/sda3 across to as far left as it will go.
How Can I do that?, I tried in Gparted, but i can not move that partition, or should boot the pc and start with the CD where GParted is ?

>Then just create a partition in the unallocated space 
OK, that's mean right-click -> new, etc
>and use the rest of the tutorial you were following to achieve your separate /home
I want to add more memory to my current tome, Am i doing that with this? Sorry for my basic questions.

Thanks

---

### Post by Clay_Banger on 2007-06-05
im a little confused, could you give me some information with the the sda1-3 and what it is used for?

like this:
sda1 = /
sda2 = /home
sda3 = swap
sda4 = winxp

---

### Post by bren on 2007-06-05
Hi cseljatib

OK 2 quick things that will help you - you are not far from achieving what you want

1) look at your screenshot again in #1.    See all those padlocks - you cannot edit these volumes because they are already mounted in the version you are running.     If you boot fr om the LiveCD or even better the System Rescue CD mentioned in the thread below then you can change partitions as you need

[http://ubuntuforums.org/showthread.php?t=465442](http://ubuntuforums.org/showthread.php?t=465442)

2) Post #2 is right you need to juggle extended partions and make logical partions within the extended partion.

3) So try deleting the small extended partion you have right now (if there is nothing there)
Then right click the unallocated and create a new extended
Within the extended create a swap and a home partition

Good luck

Bren

---

### Post by cseljatib on 2007-06-05
I am just a beginner in ubuntu, then I really do not know, but here is what i think they are

sda1 = where winxp is
sda2 = ????? (I do not know)
sda3 = /home
sda4 = ????? (I do not know)
sda5 = linux-swap

notice that as in the pic1 appear, sda4 is an "extended" Filesystem, and sda5 is "within" sda4.

What should I do?, reboot and start with the Gparted CD?? or ??

thank you very much

---

### Post by Clay_Banger on 2007-06-05
i was under the assumption you were using the livecd, try with that and see how you go.

---

### Post by bren on 2007-06-05
yep csel

boot ubuntu from the livecd (not hard disk)
go to system - admin - Gnome partition editor and you can change partitions to sizes you need
the graphical example in post #2 is what you are aiming for

bren

---

### Post by cseljatib on 2007-06-10
I have tried with booting from the Live CD and then GNOME edition partition, but I can NOT move the partition \sda3 as shown in post #2, then I cannot do any further try. How did you do it?

What more do you suggest me?, please give me details about it (if i need to do it from the LiveCD, or in the terminal, etc)

PLEASE, help me!!!

---

