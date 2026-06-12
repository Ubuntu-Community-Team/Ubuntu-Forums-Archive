---
title: "Windows stuck at &quot;starting up...&quot; please help."
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by dcbtfoabaaposba7 on 2006-11-06
Hey you guys, im new to linux and heres the deal
please try to help

last night i finally install ubuntu and i manually partitioned the harddrive so i can still run windows at a later time. Ubuntu works fine but when i try to boot my computer with windows, the compter says "starting up" at the top left and doesnt get any further. It doesnt freeze as theres a blinking line underneath, but it just doesnt "start up". I was wondering if theres anything i can do to get it to boot, or if theres anyway to retrieve my files from the windows partition using  ubuntu. If there's any other information you guys might need just ask. I'll try to hang around these forums all day after school. If you could help or at least lead me to the right direction i would truely appreciate it. thanks beforehand.

---

### Post by Ecthelion on 2006-11-06
Normally your windows partition should be mounted in Ubuntu...

Since you can see your mounted disks on your desktop (except if you didn't used the standard mountpoint)(which you probably didn't) you should just double click on the windows partition to acces it...

Reading NTFS is standard in Ubuntu, it's only for writing that you have to install more things.

Dunno how to fix your windows startup problem though

---

### Post by caravel on 2006-11-06
You said you'd partitioned manually, so you may have removed part of the windows partition by mistake, when you were resizing the partitions. :-?

---

### Post by jkvv_1973 on 2006-11-06
hehe...windows had an accident...

yea it would have been better for an auto partition/resize partition by Ubuntu...manual probably took a bite @ the windows partition causing irreparable damage...if you still have a xp windows disc you might wanna do a "repair windows" install (but I really do think you should have posted this in a windows forum)

---

### Post by dcbtfoabaaposba7 on 2006-11-08
im able to access the partition from Ubuntu im just not able to boot the OS. Is that a good thing? will i be able to fix this? thanks

---

### Post by Sef on 2006-11-08
> im able to access the partition from Ubuntu im just not able to boot the OS. Is that a good thing? will i be able to fix this? thanks

What is the partition file system? (NTFS, FAT32, ext3, reiferfs, etc.)

---

### Post by dcbtfoabaaposba7 on 2006-11-08
ehh.. i feel kinda stupid for asking but how can i find out?

---

### Post by bulldog on 2006-11-08
> **dcbtfoabaaposba7 said:**
> ehh.. i feel kinda stupid for asking but how can i find out?

Give us the outcome of```
sudo fdisk -l
``` l as like

You can always try to repair your windows boot.
If you have a windows cd you can boot from it till you get the options,install,repair or leave.
Choose the repair option which brings you to a terminal screen.
Choose the windows you want to repair and use fixboot and/or fixmbr.

If this works and you can boot windows again then you have to reinstall GRUB to boot Ubuntu.
This is done with the live cd.Boot the live cd,
```
When you get to the desktop open a terminal and enter. 

[code]sudo grub
```

This will get you a "grub>" prompt 

```
find /boot/grub/stage1
```

This will return a location. Use that location in the next line 

```
root (hd?,?)
```

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Exit the grub shell

```
quit
```

Grub will be installed to the mbr.[/code]

---

### Post by dcbtfoabaaposba7 on 2006-11-08
thank you soo much for the reply. the outcome of sudo fdisk -l was 


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       17793   142922241   82  Linux swap / Solaris
/dev/hda2           17794       19098    10482412+  82  Linux swap / Solaris
/dev/hda3           19099       24320    41945715   83  Linux

Disk /dev/sda: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         965      246989+   6  FAT16

---

### Post by dcbtfoabaaposba7 on 2006-11-09
Anyone... please...

---

### Post by mangoti on 2006-11-09
Can you tell us what your setup is supposed to be drive and partition wise?
It appears that you have ubuntu installed on the first IDE disk (200G) with 3 partitions, including 2 swap partitions, and a removable media (sda, 256MB,FAT16 partition).
Is that what it supposed to be? If yes, that's sounds pretty unusual for a beginner. I suspect that you messed up your partitions because I cannot see any partition suitable for Windows. You might have changed the type of the first partition where Widows reside typically for a dual boot. In that case I dont know if you will be able to reverse it without damage.

Good luck.

---

### Post by Darkhematite on 2006-12-10
Hello, I am new to Linux and bran new to the board.  I am having the same problem although I used the automatic partition tool while installing Linux on a clean windows install.  When I run Fdisk this is what I get


Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         902     7245283+   7  HPFS/NTFS
/dev/hda2             903        2367    11767612+  83  Linux
/dev/hda3            2368        2434      538177+   5  Extended
/dev/hda5            2368        2434      538146   82  Linux swap / Solaris

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1      484521   244198552+  55  EZ-Drive


I tried to fix the windows install with fixboot and fixmbr and reinstalling Grub but to no avail.  After countless Google searches I still haven't found a solution to this problem.  Any info or pointers to information would be greatly appreciated.  

Just to reiterate when selecting Windows XP Professional from the Grub menu I get a "Starting Up ....." message with a blinking light but that is all.  Thanks in advance.

---

### Post by Ecthelion on 2006-12-11
Hey,

> I tried to fix the windows install with fixboot and fixmbr and reinstalling Grub but to no avail. After countless Google searches I still haven't found a solution to this problem. Any info or pointers to information would be greatly appreciated.

When you use the windows disk to repair the grub gets removed...
But does the windows startup work before you put grub back on it?

If not, then I'm afraid you need to be on a windows forum...

---

### Post by Darkhematite on 2006-12-11
Thanks for the tip but re installing windows late last night worked.  Then I just had to install Grub again.  Again thanks

---

