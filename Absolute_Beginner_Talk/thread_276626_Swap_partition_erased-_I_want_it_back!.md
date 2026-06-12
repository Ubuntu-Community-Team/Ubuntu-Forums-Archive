---
title: "Swap partition erased- I want it back!"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by martinrandau on 2006-10-13
Hi
I thought I should check out the new mandriva 2007 release so I made some room from my windows partition and installed it. Now I realised that it must have reformatted my swap partition into ext3! 

What I have done so far is to use fdisk to erase all mandriva partitions (including the old swap partition) and made a new swap partition. In fstab it is /dev/hda5 so I made an extended partition /dev/hda4 and then a swap on /dev/hda5. At boot I get a message saying "swapon: /dev/hda5: Invalid argument" and this also what I get when I run the command. 

The system monitor confirms that I run with no swap (0 bytes of 0 bytes). The disks manager says "free space not available" for /dev/hda5 (I guess this is correct).

My question is, what shall I do to get my swap back and why do I get this message?

PLEASE HELP

---

### Post by Kateikyoushi on 2006-10-13
If you give us the output of these lines we can set it up.

```
sudo fisk -l
```

Then your stab

```
cat /etc/fstab
```

---

### Post by martinrandau on 2006-10-13
Hi,
thank you so much for your help. Here are the outputs as required:

```
martin@yeah:~$ sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   12  Compaq diagnostics
/dev/hda2   *         638        3953    26635770    c  W95 FAT32 (LBA)
/dev/hda3            5207       14216    72372825   83  Linux
/dev/hda4            3954        4440     3911827+   5  Extended
/dev/hda5            3954        4440     3911796   82  Linux swap / Solaris

Partition table entries are not in disk order

```

```
martin@yeah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by anaconda on 2006-10-13
those files seem to be in order.

have you already tried:
```
sudo mkswap /dev/hda5
sudo swapon /dev/hda5
```

(dont know if the "sudo" is really necessary, but it wont hurt..)
The swapon -command is needed only once.. since you have your swap in fstab -file, swapon is run automatically with each boot

then check with 
free
that your swap is actually in use..

---

### Post by martinrandau on 2006-10-13
```
martin@yeah:~$ sudo mkswap /dev/hda5
Password:
Setting up swapspace version 1, size = 4005675 kB
no label, UUID=280d1a7b-321a-40f7-9368-f3744ee2f1f0
martin@yeah:~$ sudo swapon /dev/hda5
martin@yeah:~$ free
             total       used       free     shared    buffers     cached
Mem:       1033252     490652     542600          0      12904     302820
-/+ buffers/cache:     174928     858324
Swap:      3911788          0    3911788
```

So yeah this indeed worked! So I don't have to do anything additional to activate it each boot?

Thank you so much for your help.

---

