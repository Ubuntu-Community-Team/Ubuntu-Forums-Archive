---
title: "data recovery, URGENT"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by mkuhac on 2006-12-19
I accidentally copied file(cp) from my home directory to /dev/hda1 which was my ntfs partition with xp.
Now I can't boot into windows any more, or mount the partition from ubuntu.
I have no idea how to recover ntfs partition. Please help I'm desperate.

---

### Post by aysiu on 2006-12-19
That could be bad, but all is probably not lost. Let's take it one step at a time.

Can you post the output of this terminal command? ```
sudo fdisk -l
```

---

### Post by mkuhac on 2006-12-19
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4905    39399381    7  HPFS/NTFS
/dev/hda2            4906        9832    39576127+  83  Linux
/dev/hda3            9833        9964     1060290   82  Linux swap / Solaris

---

### Post by aysiu on 2006-12-19
Good. At least you didn't lose your partition table on that drive--but even that would have a fix.

Let's try to mount it. I know you said you couldn't mount it, but I'd like to mount it from the terminal and just see what errors we get. If we can't mount it, then we may have to use *ddrescue*. Can you paste these commands into the terminal and then post back all the output (errors, non-errors, anything)? ```
sudo umount /dev/hda1
sudo mkdir /media/recovery
sudo mount -t ntfs /dev/hda1 /media/recovery -o nls=utf8,umask=0222
cd /media/recovery
ls
```

---

### Post by mkuhac on 2006-12-19
Thank you for your quick response. Here's the output:

root@mkuhac-desktop:/home/mkuhac# sudo umount /dev/hda1
umount: /dev/hda1: not mounted
root@mkuhac-desktop:/home/mkuhac# sudo mkdir /media/recovery
root@mkuhac-desktop:/home/mkuhac# sudo mount -t ntfs /dev/hda1 /media/recovery - o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@mkuhac-desktop:/home/mkuhac# cd /media/recovery
root@mkuhac-desktop:/media/recovery# ls
root@mkuhac-desktop:/media/recovery#

---

### Post by aysiu on 2006-12-19
I think *ddrescue* might be your best option. I'm not sure if you can use it or not, because it'll require you to have enough disk space to back up your entire NTFS partition. Do you have that much disk space... either on Ubuntu or on an external hard drive?

---

### Post by mkuhac on 2006-12-19
I have enough free space. What should I do with ddrescue?

---

### Post by aysiu on 2006-12-19
First, make sure you have the Universe repositories enabled. If you don't, you can get extra repositories by following this HowTo:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Next, install *ddrescue*: ```
sudo aptitude update
sudo aptitude install ddrescue
``` Finally, use it. Let's assume, for the sake of these instructions, that you have enough room inside your home directory to make a backup copy of your NTFS partition. If not, just substitute in whatever directory you do have space in. ```
sudo dd_rescue /dev/hda1 ~/hda1.img
``` This will take a while, depending on how fast your computer is and how much data you have on your NTFS partition. Then, you can mount the backup: ```
sudo mount -t ntfs ~/hda1.img /media/recovery -o nls=utf8,umask=0222
``` and get the files from /media/recovery using Nautilus or Konqueror.

I don't fully understand *ddrescue*, but I believe it skips bad blocks and copies the partition byte by byte instead of file by file. Please also note that (for some crazy reason), the package name is *ddrescue* but the command name is *dd_rescue*.

---

### Post by mkuhac on 2006-12-19
Wait a second. ENTIRE ntfs partition? No. Ext3fs and ntfs on my computer were almost equal in size. But I have about 30 GB free space on linux and (had) about 20 free on ntfs. And i don't have any external hd-s.

---

### Post by aysiu on 2006-12-19
Hm. I'm not sure what would be the next best thing, then. You have 30 GB free on Ext3, but your NTFS partition is more than 30 GB, huh?

I'm hoping someone else will jump in here with a brilliant solution.

---

### Post by mkuhac on 2006-12-19
Is there a way to somehow compact ntfs partition (half of it's space was unused anyway)?

---

### Post by aysiu on 2006-12-19
> **mkuhac said:**
> Is there a way to somehow compact ntfs partition (half of it's space was unused anyway)?
Oh wait a second--I'm not 100% sure about this, but I don't think *ddrescue* will copy the unused parts of the NTFS drive.

I'll need someone more knowledgeable to jump in and confirm that, though.

---

### Post by John E on 2006-12-19
**mkuhac** - Have you tried booting up from the XP install CD and selecting 'R' for recovery mode?

---

### Post by mkuhac on 2006-12-19
No, but I don't know how to use recovery console.

---

### Post by John E on 2006-12-19
I'm a bit hazy myself but if I remember correctly, it boots up to a command prompt. You then type **fixboot** and it will ask you which parttiion you want to boot from (the first partition, as far as I can tell from your previous posts).

Next, type **fixmbr** and with a bit of luck, you'll be able to boot up into XP. Once you're into XP, you can re-install Grub to get yourself back into Ubuntu, too. Don't worry too much about the various dire warnings you'll see along the way but naturally, you'd be better off if you could back up your data first..

Of course, all this assumes that you didn't corrupt some valuable XP files. What exactly did you copy?

---

### Post by mkuhac on 2006-12-19
I don't see why is it important what I copied, but anyway it was a xp driver for old Genius usb cam (only 47KB uncompressed).

---

### Post by christhemonkey on 2006-12-19
@**mkuhac** On the previous page, you pasted the output of this command:
> sudo mount -t ntfs /dev/hda1 /media/recovery **- o** nls=utf8,umask=0222


When aysiu asked for this one:
```
sudo mount -t ntfs /dev/hda1 /media/recovery **-o** nls=utf8,umask=0222

```

Which might have led to that error message.
Please could you try the initial command and let us know the output.

(i realise its might just be a typo though!:D)

---

### Post by John E on 2006-12-19
> **mkuhac said:**
> I don't see why is it important what I copied, but anyway it was a xp driver for old Genius usb cam (only 47KB uncompressed).

It's important because Windows & Linux sometimes share file names. For example, **fdisk** is common to both - but a copy of **fdisk** written for Linux wouldn't work under Windows or vice versa. Therefore, you might have copied a driver, overwriting the Windows version with a Linux version, thereby preventing boot-up.

However, from what you've said, it doesn't seem as though you've done any major damage. I'd be tempted to use the XP recovery option and then re-install Grub.

---

### Post by mkuhac on 2006-12-19
I tried with xp recovery, and it worked. But now I need to restore grub (and linux). oh, and I forgot to mention one thing: I don't have floppy disk drive. And another thing: now xp is acting wierd.
To John E: i did't copy driver from directory on ext3 partition to some dir on ntfs, instead I copied driver on ntfs partition itself (my entire ntfs partition was unaccessibile after that). Also the usb cam driver itself was in self-extracting executable(but I didn't run it - even if I wanted to I was still in ubuntu). So you see the file that I copied has absolutely no relevance.
Here is even more bizzare thing that happened after: on ubuntu, I downloaded and ran program named TestDisk, and it reported some weird errors: that it can recover my ntfs partition, but not ext2fs (from which it was running??). Of course I didn't do/save anything with TestDisk, I just quit it.

---

### Post by mkuhac on 2006-12-19
Thank you all for your time, but I give up. Since my computer can (barely) boot into xp, I'll copy all my data on cd-s and repartition disks and reinstall everything.

---

### Post by nsleiman on 2006-12-19
if xp recovery worked, try if you want to boot up your machine with the ubuntu disk and just go to the grub installation part (maybe you need to mount also the partitions on your disk). i passed through this some time ago and it worked fine with me.

---

