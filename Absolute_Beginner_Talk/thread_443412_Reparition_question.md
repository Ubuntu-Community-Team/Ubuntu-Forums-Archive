---
title: "Reparition question"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-05-14
Is it possible to take space from my windows NTFS partition and add it to my / partition?

My current hard drive partitions:
Sda1 - NTFS - 28 GB
Sda2 - Extended with NTFS (140 GB), Swap (1 GB) and / (5 GB)
Sda3 - /home - 15 GB.

Thanks, Chris

---

### Post by dannyboy79 on 2007-05-14
> **cawill said:**
> Is it possible to take space from my windows NTFS partition and add it to my / partition?

My current hard drive partitions:
Sda1 - NTFS - 28 GB
Sda2 - Extended with NTFS (140 GB), Swap (1 GB) and / (5 GB)
Sda3 - /home - 15 GB.

Thanks, Chris

of course this is possible. It's always a good idea to backup any critical data to be on the safe side but all you would have to do is shrink NTFS and grow ext3. Now others may tell you to do it while you're in Ubuntu but to be on the safe side and so you don't affect anything while Ubuntu is running just pop in your the Live CD. I don't think Gnome Partition Editor is on their but you can easily download into your ramfs filesystem and then you can run it. Like I said, just shrink NTFS to the amount that want, then hit apply so it applies that command to the NTFS partition, then just click on the Ext3 partition and grow it and hit apply and it'll do it. then simply shutdown the live cd and you should be set.

---

### Post by az on 2007-05-14
Yes, you can resize both NTFS and ext3 partitions.  You cannot change the beginning point of a partition.  You would need to shrink the 140 GIG partition by enough to be able to copy the entire / partition onto the free space, delete the original and then extend the partition from the end.  

You need to do this from the live cd, since no partition can be mounted on the drive you are modifying.  You even  need to unmount your swap since the live cd will use it if it finds one.

sudo swapoff -a

Change your mountpoints if you need to.  Look in /etc/fstab and change the numbering, if appropriate.

---

### Post by dannyboy79 on 2007-05-14
> **az said:**
> Yes, you can resize both NTFS and ext3 partitions.  You cannot change the beginning point of a partition.  You would need to shrink the 140 GIG partition by enough to be able to copy the entire / partition onto the free space, delete the original and then extend the partition from the end.  

You need to do this from the live cd, since no partition can be mounted on the drive you are modifying.  You even  need to unmount your swap since the live cd will use it if it finds one.

sudo swapoff -a

Change your mountpoints if you need to.  Look in /etc/fstab and change the numbering, if appropriate.


i don't follow your advice? He has an extended partition that is 140gb in size, the NTFS partition is partition 3 if his partition 2 is the extended one. so why can't he just shrink his NTFS down to 100 gb and then just take that extra space and add it to his /. a partition will grow forward, I have done it. I used the Gparted live cd but I don;t see why a live cd wouldn't do it also.

---

### Post by cawill on 2007-05-14
Hi, thanks for your help so far.

I'm using the ubuntu live cd with gparted but when I resize the NTFS partition it says its mounted, so I unmount it and it still says its mounted, how do I fix this?

---

### Post by Big_Croc7 on 2007-05-14
I'd recommend using the GParted Live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)), this is a Live CD that boots with only one job - to run GParted.  It has more features than the version that comes with Ubuntu, and it won't use any swap space.  I think it is capable of moving the start point of a ext partition as well, though this depends on the format type (e.g. it works with FAT, but not with XFS - not sure about ext3).

Also, you can safely modify/delete and recreate the swap partition as you wish without losing data.

---

### Post by cawill on 2007-05-14
Hi, would using the Gparted Live CD fix my problem of not being able to unmount the NTFS Partition?

---

### Post by dannyboy79 on 2007-05-14
> **cawill said:**
> Hi, would using the Gparted Live CD fix my problem of not being able to unmount the NTFS Partition?

it wouldn't be mounted in the first place. live cd's normally mount all hard drives and partitions and that's most likely why the ntfs partition was mounted. also, have you tried to issue this command after hitting **alt f2**. **sudo unmount /dev/whateverdriveis **(/dev/whateverdriveis can be found by issuing sudo fdisk -l at the command line or terminal and just look for all the partitions that state NTFS) but again, as I suggested and another suggested, use the Gparted live cd.

---

### Post by cawill on 2007-05-14
I used the Gparted Live CD to reformat partitions successfully, but now Grub doesn't work. What is the easiest way to restore/reinstall Grub?

---

### Post by dannyboy79 on 2007-05-14
> **cawill said:**
> I used the Gparted Live CD to reformat partitions successfully, but now Grub doesn't work. What is the easiest way to restore/reinstall Grub?
this is NOT good. if all you did was move space around and you DIDN'T change any partitions around, then something got messed up. You partition table should be the same except just different sizes. Anyway, try this. Boot up the live cd, then go to a command line, and do, 

```
sudo grub
```
this will get you into the grub cli.

type
```
find /boot/grub/stage2
```
this should return something like (hd0,1) or whatever. now we know where grub's files are located. we just need to reinstall it to the mbr of the drive that you're booting from your bios.
```
root (hd0,1)
``` 
NOTE: enter the same exact thing that the find command returned.
```
setup (hd0)
```
NOTE: this will overwrite that drives Master boot record so if you have any special boot manager or anything like that grub will overwrite the first 400 some kb of the hard drive! the only part of the mbr that doesn't get overwritten is the partition table. now type
```
quit
```
now grub should be installed and you should be able tyo reboot using grub now. we may need to readd any os's that you had added previously just post back and I can help. also, please post the results of these commands as well IF you post back as i'll need the info anyway.

```
sudo fdisk -l
```
with the fdisk info, please put what os's are where and what the partitions have on them...

```
cat /boot/grub/menu.lst
```

```
cat /boot/grub/device.map
```
If any commands fail, try to use sudo with them.

---

### Post by cawill on 2007-05-14
What caused the problem I think was the fact that I had to delete my swap file to be able to add more space to my / partition and then create a swap file again.

Managed to fix the problem quite quickly afterwards though and everything is working fine now. Thanks for your help.
Chris

---

### Post by dannyboy79 on 2007-05-14
> **cawill said:**
> What caused the problem I think was the fact that I had to delete my swap file to be able to add more space to my / partition and then create a swap file again.

Managed to fix the problem quite quickly afterwards though and everything is working fine now. Thanks for your help.
Chris

yeap, you'r right, I saw that after I re-read what exactly you were planning on doing. glad you're all set!

---

