---
title: "Moving Grub"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Videofolife13 on 2007-12-02
Hey guys,
So I'm completely new to this whole Linux thing. I just got an external Hard Drive and decided I'd see what this whole Ubuntu and Fedora thing was about. So here's what I have for a set up:

320 GB External Hard Drive
>10GB for Ubuntu (ext2)
>10GB for Fedora (ext2)
>20GB for Extra Stuff (FAT32)
>The Rest for Everything Else(FAT32)
80GB Internal Hard Drive, No partitions, just for Windows XP

So all of the operating systems are installed fine, but when I installed Fedora after Ubuntu, it sent me to the fedora version of Grub with no Ubuntu entries. So I just spent an hour fixing that. Now I have my boot loader all set up. Here's my issue. I understood that Fedora and Ubuntu were dependent on a Bootloader like GRUB. Fine. But I didn't know that XP would then be dependent on the same bootloader. GRUB is installed on both my Fedora partition and my Ubuntu partition, but the one on the Fedora Partition boots by default. When I unplug my external hard drive, Windows can't boot, because there is no GRUB on my internal hard Drive.

So I need to know how to put GRUB on my internal Hard Drive, AND more importantly have it boot by default over the two other GRUBs that are installed. I saw some stuff about installing GRUB from the live Ubuntu CD. Could I partition a small portion of my Internal Hard Drive (safely) and put GRUB from the live Ubuntu CD to that newly Partitioned portion of the Hard Drive?

Any and all help is appreciated.
Thanks guys,
-Video

---

### Post by gazj on 2007-12-02
i am not sure if you can do that without at least have one ext2/ext3 (linux) partition on your internal hard drive.

you could however restore the windows bootloader on your internal drive with you windows cd

Start booting from your xp cd then choose recovery console when prompted

use the command
```
fixmbr
```
and
```
fixboot
```

not: you can also so this from a windows 98 cd, just select command prompt when asked, then use

```
fdisk /mbr
```

you should now be able to reboot into windows, and hopefully grub will only come up when you have your usb drive inserted.

---

### Post by meierfra on 2007-12-02
Don't follow the suggestions in the previous  post, since you won't be able to boot into Fedora anymore.  To solve your "boot without external drive"  problem click on DualTwo in my signature. To add ububtu to the fedora "grub menu" see
[http://ubuntuforums.org/showthread.php?t=629386]("http://ubuntuforums.org/showthread.php?t=629386")

If you need help, adjusting the numbers. Post the output of 
```

sudo fdisk -l
```
(l is a lowercase L)

and ```
cat /boot/grub/menu.lst
```


(Edit: If you did already  use "FixMBR" it is not a big deal. The problems can still be fixed, but you'll have to use the Ubuntu or Fedore  LiveCD)

---

### Post by Videofolife13 on 2007-12-02
Hmm.. I was about to say, I just did that and I can't get into Fedora or Ubuntu, or Grub... Any solution to that?
-Video

---

### Post by dadawan on 2007-12-02
> So I need to know how to put GRUB on my internal Hard Drive, AND more importantly have it boot by default over the two other GRUBs that are installed.

> i am not sure if you can do that without at least have one ext2/ext3 (linux) partition on your internal hard drive.


Gazj is exactly right.   

  Just in case it isn't clear,  Grub actually needs to read a config file from a partition on your hard drive.  So what frequently happens is people decide they don't want Linux any more, and they nuke their Linux partition and Grub can't find the config file any more.   Resulting in a machine that no longer boots Windows nor Linux  :(


  On my Linux installs I think it is usually /boot/grub/menu.lst

  But I'm not sure what partition types Grub can read.  I doubt for example you can put your menu.lst config file on your Windows NTFS partition for example.   On my system I made a little ext3 partition just for Grub, so that if something happened to my Linux partition I could still boot.

  Maybe you could do something similar..

-Kevin


  Anyway I

---

### Post by meierfra on 2007-12-02
Boot from the Ubuntu (or Fedore LIveCD) and open a terminal and post the output of

```
sudo fdisk -l
```

---

### Post by Videofolife13 on 2007-12-02
Here is the output

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00890089

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       33815   271618956    7  HPFS/NTFS
/dev/sdb2           36366       37639    10233405   83  Linux
/dev/sdb3           37640       38913    10233405   83  Linux
/dev/sdb4           33816       36365    20482875    7  HPFS/NTFS

Partition table entries are not in disk order

```

-Video

---

### Post by meierfra on 2007-12-02
To this from a LiveCD


Step 1) Edit ubuntu "menu.lst:

 Open a terminal and type

```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb2 /ubuntu
gksudo  gedit  /ubuntu/boot/grub/menu.lst
```

change

"#groot (hd1,1)" to "#groot (hd0,1)"

change all  "root (hd1,1)"  to root "(hd0,1)"

Add this to the end

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1


title Fedora
configfile (hd0,2)/boot/grub/menu.lst

(if you already had a windows item remove it)

Save and close the file.

Step 2) Edit Fedora's menu.lst

In the terminal


```
sudo mkdir /fedora
sudo mount -t ext3 /dev/sdb3 /fedora
gksudo  gedit  /fedora/boot/grub/menu.lst
```

#groot (hd1,2)" to "#groot (hd0,2)"

change all  "root (hd1,2)"  to root "(hd0,2)"


Save and close the file.

Step 3: Install Ubuntu's Grub to the MBR of the external drive:



```
sudo grub

```
and at the "grub>" prompt



```
root (hd1,1)

setup (hd1)

quit
```


Step 4  Reboot with the external drive first in the boot order in the bios.

---

### Post by Videofolife13 on 2007-12-02
While trying to get the menu.lst from the Ubuntu drive through the terminal, I just get a blank document. I tried to retrieve the file manually but it would not let me save over the original file. I'll try to copy and paste the text from the manually found list into the new list. 
-Video

It says I don't have permission to write to the folder in question.

---

### Post by meierfra on 2007-12-02
Most probably you just had a typo somewhere in this part of the instruction:

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sdb2 /ubuntu
gksudo  gedit  /ubuntu/boot/grub/menu.lst



Just to double check:  sdb2 is your ubuntu partition ? and sdb3 is your Fedora partition

---

### Post by Videofolife13 on 2007-12-02
When I type this:
```
sudo mount -t ext3 /dev/sdb2 /ubuntu
```
I get:
```
mount: /dev/sdb2 already mounted or /ubuntu busy
mount: according to mtab, /dev/sdb2 is mounted on /media/disk

```

What?

The next command still gives me a blank document
Video

This is the whole Terminal "transaction"

"ubuntu@ubuntu:~$ sudo mkdir /ubuntu
mkdir: cannot create directory `/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb2 /ubuntu
mount: /dev/sdb2 already mounted or /ubuntu busy
mount: according to mtab, /dev/sdb2 is mounted on /media/disk
ubuntu@ubuntu:~$ gksudo gedit /ubuntu/boot/grub/menu.lst"

---

### Post by meierfra on 2007-12-02
Use 

```

gksudo gedit /media/disk/boot/grub/menu.lst
```

---

### Post by Videofolife13 on 2007-12-02
that's the one. Let me finish this up.
-Video

 Done. It works. This just reworked which hard Drive booted first, right? Thanks a lot. I really appreciate it.

---

### Post by meierfra on 2007-12-02
> one. It works. This just reworked which hard Drive booted first, right? 

Yes. (and you added Fedora to the Ubuntu menu.lst)

> Thanks a lot. I really appreciate it.

You are welcome.

---

### Post by 2vack on 2008-01-22
Hi,

Im also one of the many new users of ubuntu. and I'm having the some problem with my boot loader.

I have 2 disks, a 40GB and a 160 GB. the 160 GB should be my primary boot disk since it contains all my OS (UBUNTU & XP) and the 40 GB is a NTFS that server as a backup of my system. the problem is, when i setup ubuntu . GRUB was installed on my 40 GB disk, So when I remove it from my system, GRUB does not start at all and my system boots automatically to XP. 

My fdisk output is
jeffrey@2vack:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100       15140    80654332+   f  W95 Ext'd (LBA)
/dev/sdb3           15141       19457    34676302+  83  Linux
/dev/sdb5            5100       14949    79120093+   7  HPFS/NTFS
/dev/sdb6           14950       15140     1534176   82  Linux swap / Solaris
jeffrey@2vack:~$ 

can somebody help me with the sudo commands to move my grub to the right disk? it should be on 
Disk /dev/sdb

teach me oh gurus please.

thank you.

---

