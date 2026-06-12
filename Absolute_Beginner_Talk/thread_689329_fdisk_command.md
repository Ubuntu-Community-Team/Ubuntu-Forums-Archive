---
title: "fdisk command ?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-02-06
Does anyone ever use the fdisk command for anytihng other than "fdisk -l" ?
I know there is Gparted but I'm just curious if anyone ever uses it since the command line is so prevalent in Linux. MS DOS fdisk was very easy to use but I just never hear anyone talk about using  fdisk in Linux. I don't have any specific task I need to do now but I may eventually delete my XP partition & I would like to know it could safely be done with fdisk.

---

### Post by Gen2ly on 2008-02-06
IMHO, fdisk is a great program.  It appears abstract at the beginning but learning to use it can make a quick job of partitioning - not good for resizing I believe but good for developing an original partition map.

---

### Post by dgray_from_dc on 2008-02-06
I use fdisk all the time.  When I set up my RAID array, I used fdisk to create the partitions and mark them as type fd (Linux RAID).

Since I use KDE and Xfce, (Kubuntu & Xubuntu) I tend not to use GParted.  Besides, I learned fdisk before I was aware of anything else having come from the Win9x/DOS environment.

---

### Post by oedha on 2008-02-06
when i run fdisk --help...here is the output
oedha@The-ELF:~$ fdisk --help
fdisk: invalid option -- -

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
oedha@The-ELF:~$

---

### Post by dannyboy79 on 2008-02-06
> **garyed said:**
> Does anyone ever use the fdisk command for anytihng other than "fdisk -l" ?
I know there is Gparted but I'm just curious if anyone ever uses it since the command line is so prevalent in Linux. MS DOS fdisk was very easy to use but I just never hear anyone talk about using  fdisk in Linux. I don't have any specific task I need to do now but I may eventually delete my XP partition & I would like to know it could safely be done with fdisk.
man fdisk
will show you what fdisk in linux can all do. MS DOS fdisk and fdisk in linux are different however. fdisk can surely delete your windows xp partition, you can then create a new one and then use mkfs to create a new filesystem on that partition. the great thing about Gparted is that it's all done in one nice little gui.

---

### Post by anaconda on 2008-02-06
Yep.. I have used fdisk sometimes, but cfdisk is better, and if nothing else works then sfdisk propably will..

---

### Post by garyed on 2008-02-06
I'vre tried man fdisk but there's a part in there that says "fdisk is a buggy program that does fuzzy things -  usually it happens to produce reasonable results." 
That was one of the reasons for this post.

---

### Post by Keith Hedger on 2008-02-06
Fdisk is about the only thing i can use on linux to parttition my ipod (I fiddle with ipl and rockbox!)

---

### Post by hyper_ch on 2008-02-06
and in ubuntu you have to use
```

sudo fdisk -l

```

---

### Post by bilge.tutak on 2008-02-06
You can use fdisk to list/modify your existing partition table. For this purpose you have to give the disk as a parameter to the fdisk like
$>fdisk /dev/hda
Your disk might be different /dev/???.
Then it has a text based menu you can navigate through.
p will print the current partition table with information (active, file system type, size etc.)
Other letters are available for playing around.
Just be careful what you are doing. Especially when deleting :). If you do something wrong, just exit without saving your partition table.
Good luck deleting your windows partition :D

---

### Post by andrewjoy on 2008-02-06
if you are experanced with DOS fdisk command then you may be better off with cfdisk

```
sudo cfdisk
```

---

### Post by garyed on 2008-02-06
So I guess it works fine as long as you know what you're doing.
I think I'll try & find a good tutorial on fdisk & check it out.
Thanks for all the replies.
By the way I'm running Feisty

---

