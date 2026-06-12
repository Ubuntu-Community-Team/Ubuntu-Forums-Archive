---
title: "dual boot win xp and ubuntu"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by waxfactor2nd on 2006-09-30
hi ive never used linux before, but everyone have to start at one point. ive chosen ubuntu to try, but i want to dual boot with windows xp. ive done as ive been guided, first installed windows xp on hdd 0 partition 1, then ive taken ubuntu and taken use the largest continuous free space and installed it. there where no problems. but when i now reboot my computer,it says grub loader 1.5
grub loading
grub error 22

before i can choose windows or linux.. now i dont know what i shall do.. can someone help me. im trying to install ubuntu 6.06lts for pc, and i have a amd atlhon 64 3700+, a8n-sli premium, 2gb ram, and two 250gb spinpoints (sata) (both linux and windows have to go on the first one.)

how shall i do??

---

### Post by bulldog on 2006-09-30
Error 22 means this,

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

As you can see here,

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

You can mount your hdd into the live cd.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda? /mnt/ubuntu 
```


When you type in your terminal ```
sudo fdisk -l
``` l as in like,you can see how your partitions are named.

You can compare with your menu.lst ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by waxfactor2nd on 2006-09-30
> **bulldog said:**
> Error 22 means this,

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

As you can see here,

[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)

You can mount your hdd into the live cd.

```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda? /mnt/ubuntu 
```


When you type in your terminal ```
sudo fdisk -l
``` l as in like,you can see how your partitions are named.

You can compare with your menu.lst ```
gksudo gedit /boot/grub/menu.lst
```

im sry but i dont understand it / im a very newb can you tell me what you mean??

---

### Post by bulldog on 2006-09-30
Well basicly is the info which GRUB needs to boot is not correct.

The partition info can be found by mounting your hdd in a live cd session,so you can determine how the hdd is partitioned and how they are named.

With this info you can alter GRUB [menu.lst] to correct the problems there seem to be.

---

### Post by waxfactor2nd on 2006-09-30
when i type sudo fdisk -l i get this data:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9561    76798701    7  HPFS/NTFS
/dev/sda2   *        9562       29644   161316697+  83  Linux
/dev/sda3           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3            8548       11097    20482875    7  HPFS/NTFS
/dev/sdb4           11098       30401   155059380    7  HPFS/NTFS

Disk /dev/sdd: 131 MB, 131072000 bytes
16 heads, 32 sectors/track, 500 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         500      127968+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(498, 15, 32) logical=(499, 15, 32)
ubuntu@ubuntu:~$


and gksudo gedit /boot/grub/menu.lst i get this:

ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

(gedit:9195): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
 
and a empty gedit window / and because im a newb i dont understand anythingwiththsi so what shall i do?? or what shall i write where??

---

### Post by Sef on 2006-09-30
> im sry but i dont understand it / im a very newb can you tell me what you mean??

Applications > Accessories > Terminal

Once you are at the terminal, type in the directions as provided by bulldog.  Then press enter.  You will need to put in your password, and the computer will do something.  Once it finishes, enter the next line of code and press enter.

---

### Post by bulldog on 2006-09-30
If you are in a live cd session, we can install GRUB again

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
``` replace (hd?.?) with the outcome from find

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by waxfactor2nd on 2006-09-30
thx alot / i aint finished yet but it sound like it will help.. so thx

---

### Post by bulldog on 2006-09-30
> **waxfactor2nd said:**
> thx alot / i aint finished yet but it sound like it will help.. so thx

Read carefully the output you get after each command and put it in the next command the same way with spaces and hooks and all that.

You have sata disks it should be sd instead of hd watch it.

---

### Post by waxfactor2nd on 2006-09-30
i wrote exactly what you said and id didnt work / but i  just read that you wrote i should write sa instead hd / where / every where??? ive wrote hd and it didnt work

---

### Post by bulldog on 2006-09-30
> **waxfactor2nd said:**
> i wrote exactly what you said and id didnt work / but i  just read that you wrote i should write sa instead hd / where / every where??? ive wrote hd and it didnt work

When you are in GRUB and enter the commands as listed you get an answer in your terminal.
You need the answer in the next command,not just type what I wrote!!!

if you type find /boot/grub/stage1   you get something in terminal (sda2) 

Then you use (sda2) in the next command.

And so on till you reach the end.


You had error 23 what stands for,

23 : Error while parsing number
    This error is returned if GRUB was expecting to read a number and encountered bad data.

If you reboot and it still won't work I want to know some extra things,but I'm sorry, go to sleep a couple of hours and be back when I wake up.

---

