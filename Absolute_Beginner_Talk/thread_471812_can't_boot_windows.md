---
title: "can't boot windows"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by banda on 2007-06-12
i think i have messed up my grub

i was trying to get gfxboot to work but could not do it ..

 i followed instructions from, [here]("http://ubuntuforums.org/showthread.php?t=208855")

when i could not do it i went to package manager and installed the old grub

now when i try to boot xp i get the stage2readerror

help

---

### Post by dstew on 2007-06-12
It think you will have to set up grub again. To do it, boot a Live CD, open a terminal window and enter grub. Then, at the grub prompt type```
find /boot/grub/menu.lst
```Whatever it answers, use in the next command```
root (hd0,0)
```That is, if the find command returns (hd0,1), use that in the root command instead of (hd0,0). Then, re-install the grub boot loader into the Master Boot Record of the first disk```
setup (hd0)
```Quit grub (type **quit**), remove the CD and reboot. If you still get an error, post it here.

---

### Post by banda on 2007-06-12
i get this from running the commands 
(i ran these commands from the live cd but i can boot ubuntu also ... the commands on the main installation also gave the same file not founderror)


> grub> find /boot/grub/menu.lst

Error 15: File not found


---

### Post by banda on 2007-06-12
i just noticed that whenever i try to mount my windows partition in ubuntu i get the following error


[IMG]http://img53.imageshack.us/img53/3300/untitleder0.jpg[/IMG]


the partition table on my harddisk looks like this...(first one is windows , linux on ext)
[IMG]http://img61.imageshack.us/img61/6973/11111xa9.png[/IMG]

would i b able to boot into windows or have i lost the partition??

---

### Post by banda on 2007-06-12
<bump>

---

### Post by dstew on 2007-06-12
It looks like your first partition has some errors on it. You should try to fix it using the Windows Recovery Console. You access the Recovery Console from the Windows Setup CD. Boot the Windows Setup CD, and type 'R' at the first screen. When you get to the recovery console prompt, enter **chkdsk /f**. If this doesn't work there are other things we can try to fix that Windows partition.

I am not sure why grub could not find the /boot/grub/menu.lst file. From your partition table, it looks like it is on /dev/sdb6, which in grub's notation would probably be (hd1,5). When you have Ubuntu running, look in the directory to see if the file is really there.

---

### Post by Bohlio on 2007-06-12
It looks like you still have the partition just fine, but your grub is messed up... Can you install grub  off the live CD?, Not just restore it like posted above, but can you completely reinstal it? Cause that might fix it.

Edit: @dstew, How can you tell that it has errors?

---

### Post by Najand on 2007-06-12
Use:
sudo fdisk /dev/hdb
and post the output here.

---

### Post by banda on 2007-06-12
@dstew
ok i am going to try the windows recovery console
menu.lst is there ... don't know y it dosen't find it (and i did not mistype)

@bohilio
i don't know how to completely reinstall grub off live cd
and i don't know where fstab is? or what it is. i m new to ubuntu/linux

---

### Post by pnix on 2007-06-12
what's your
sudo fdisk -l /dev/hdb

---

### Post by banda on 2007-06-12
thx najand

here's the output 
> The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): 


fdisk----
> 

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2049    16458561    7  HPFS/NTFS
/dev/hdb2            2050        7530    44026132+   7  HPFS/NTFS
/dev/hdb3            7531       10387    22948852+   c  W95 FAT32 (LBA)
/dev/hdb4           10388       14593    33784695    5  Extended
/dev/hdb5           14521       14593      586341   82  Linux swap / Solaris
/dev/hdb6           10388       14520    33198259+  83  Linux

Partition table entries are not in disk order

---

### Post by Najand on 2007-06-12
I think you have removed grub, too...
Try to install it again:
```

sudo apt-get install grub

```
Then you have to edit your /boot/grub/menu.lst.
Can you post it here?

---

