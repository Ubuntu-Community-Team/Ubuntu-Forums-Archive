---
title: "Dual Boot Disater"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Grundoko on 2008-02-24
I'm a complete beginner at using linux.
I've had windows installed on my computer for a long time, using a 120gb hard drive, but i had an 80gb hard drive that wasn't being used, so i decided to pop in an ubuntu 7.04 fiesty fawn cd that i had laying in my drawer for a while. I installed it normally, and partitioned the whole 80gb hard drive.

When i restarted, it would say 
GRUB loading
ERROR 21

then it would just stop. so i reinstalled ubuntu on to my 80 gb hard drive. now, it says something like no SCSI boot record found, pick another boot device. thats not excact but it says something similar to that, it says that no matter which hard drive i am booting with.

I tried booting with a windows 98 boot floppy disk, but it says no fat32 partition was found, please partition a fat32 using a disk partitioner or somthing like that.

I know how to format my hard drive, but i have important files on it, if anyone can tell me how i can get my files off of it, so i can backup, i'd really appreciate it

---

### Post by Duck2006 on 2008-02-24
Can you get into the ubuntu install? If not run the live CD and from the terminal type

gksudo fdisk -l

and

cat /boot/grub/menu.lst

and post the outputs here.

---

### Post by Grundoko on 2008-02-24
ok i tried running the live cd, when it loaded, it showed a black screen and just played the login music over and over like a skipping sterio. my problem might be the cd, because it was just in my drawer for almost a year, its got a lot of scratches on it. but right now installing or fixing ubuntu is the least of my worries, all i'm worried about right now is getting the data off my harddrive. then i can format it without losing all my important files. any ideas?

---

