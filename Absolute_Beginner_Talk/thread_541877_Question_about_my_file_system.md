---
title: "Question about my file system"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Malhavok on 2007-09-03
Okay, I've searched quite a bit for this answer and I can't find it.  Possibly I'm wording it wrong.  Anyway, I have a relatively new compaq, p4, hyperthreaded, with Vista Basic.

I shrunk Vista's partition and installed ubuntu 7.04 no problems, and I love it.  But my question is this; Without doing anything, I am able to click on filesystem in Ubuntu and see my Vista partition (marked Compaq).  I'm able to read from it, view pictures, play music, etc...

I have recently loaded kubuntu desktop and I quite like it, but for the life of me I cannot find my windows partition inside it.  I have found articles on mounting my windows partition/hard drive, but I'm not sure if that's for me, as Ubuntu recognizes it fine.

Now, I don't care about Vista being able to see my Linux partition or not, I just want access to some of my files from Vista inside Kubuntu.  It was so simple in Ubuntu I just can't believe it would be so complex in Kubuntu.

-Malhavok

---

### Post by Obor on 2007-09-03
You can find if its mounted by 
```
sudo fdisk -l
``` in konsole/terminal.

if its not then follow the guide to mount it. You can use [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") but will have to change gedit to kate and gksudo to kdesu if you are using kubuntu. Or use the one you know of if its written for kubuntu.

---

### Post by taurus on 2007-09-03
Just add an entry in /etc/fstab and it will be mounted automatically each time you boot.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Malhavok on 2007-09-03
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13102   105238930+   7  HPFS/NTFS
/dev/sda2           17987       18532     4385745    5  Extended
/dev/sda3           18533       19457     7430062+   7  HPFS/NTFS
/dev/sda4           13103       17986    39230730   83  Linux
/dev/sda5           18202       18532     2658726   82  Linux swap / Solaris
/dev/sda6           17987       18201     1726924+  82  Linux swap / Solaris

Partition table entries are not in disk order


-Malhavok

---

### Post by taurus on 2007-09-03
From a terminal, install both ntfs-3g and ntfs-config by

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
```
Now, run ntfs-config and point it to your ntfs partitions.

```
kdesu ntfs-config
```
Once you are done, you can read and write to your ntfs filesystem with ntfs-3g driver.

---

### Post by Malhavok on 2007-09-03
Thank you everyone, especially Taurus, that app worked flawlessly.  I appreciate it.

-Malhavok

---

