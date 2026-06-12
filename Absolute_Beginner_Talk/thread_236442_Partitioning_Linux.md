---
title: "Partitioning Linux?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-14
I'm trying to repartition my internal HD so I can free-up 5GB in order to install Windows XP. What do I need to shrink my Linux partition 5GB? I have GParted and the GParted live CD, but on GParted it doesn't allow me to shrink my /dev/hda1, which is currently partitioned entirely for Ubuntu. With the live CD, i try to boot but all it says is "hw_random not detected," or something like that. Any good + safe apps available to shrink my Linux partition?

---

### Post by kpkeerthi on 2006-08-14
Well... I just needed to boot with the Live CD and use gparted to resize the partition. Not sure why it won't work for you. You may want to try [gparted live CD]("http://gparted.sourceforge.net/livecd.php") and see how it goes.

---

### Post by kbsuperstar on 2006-08-14
Like I said before, I already have the live CD.

---

### Post by kpkeerthi on 2006-08-14
OK. 2 different Live CDs here. The ubuntu Live CD and the GParted Live CD. Which one did you use? 
btw.. I used ubuntu Live CD to resize my partition and it worked fine.

---

### Post by bwayman on 2006-08-14
I do think you have to install windows XP before you  install linux.

---

### Post by kbsuperstar on 2006-08-14
I have both the GParted live CD and the Ubuntu live CD.

If you could tell me how to resize my current Linux partition (i already have Ubuntu installed) with the Ubuntu live CD, that'd be great. And is it safe to do this? I don't want to accidently erase any files on my hard drive, which is entirely partitioned to Linux.

---

### Post by kbsuperstar on 2006-08-14
bump

---

### Post by kpkeerthi on 2006-08-14
1. Boot with the Ubuntu Live CD
2. Select System -> Administration -> Gnome Partition Editor
3. Right-click the partition you want to resize and select Resize
4. Enter new size.
5. Click Resize and Apply

This will create unallocated (free) space which you might want to select from XP installer. I followed the same steps my data were intact.

---

### Post by kbsuperstar on 2006-08-14
I'll give it a try. Thanks!

---

### Post by kbsuperstar on 2006-08-14
I'll give it a try. Thanks!

---

### Post by kbsuperstar on 2006-08-14
Hey, it worked! But now comes the hard part, I believe.

If I reboot with my Windows XP installer CD in the CD-R drive and install XP onto that free space, will it take over the GRUB?

Like, post-XP-installation, if I reboot my computer, will it go to windows or Ubuntu?

If anyone has a tutorial on this, that'd be awesome! I would also like your feedback, too. Thanks!

---

### Post by kpkeerthi on 2006-08-15
Glad that it worked for you. And.. yes, XP overwrites MBR where GRUB is installed. But don't worry... There are few (simple & easy) steps you might want to do to restore GRUB. Install XP and boot using Live (ubuntu) CD and post the output of ```
sudo fdisk -l
``` and we'll proceed from there.

---

### Post by kbsuperstar on 2006-08-15
First, I'd like to thank you for the help.

I'll be sure to do that tomorrow, but right now I have to sleep. I'll install XP and post the results of the sudo fdisk -l


One thing that bothers me, though: when I boot from the Live CD, i have to change the video adapter in the BIOS 'cause it doesn't recognize my video card driver, but oh well.

'til tomorrow!

---

### Post by kbsuperstar on 2006-08-15
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2860    22972918+  83  Linux
/dev/hda2   *        2861        3497     5116702+   c  W95 FAT32 (LBA)
/dev/hda3            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris
Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11549    92759310    b  W95 FAT32
/dev/sda2           11549       11694     1164681+  82  Linux swap / Solaris/dev/sda3           11694       12188     3976087   83  Linux

```

---

### Post by kbsuperstar on 2006-08-15
Now I need to be able to boot up with GRUB, not windows. Everytime I boot it goes to windows. How do I reinstall GRUB?

I tried this ```
sudo /sbin/grub-install /dev/hda
sudo /sbin/grub-install /dev/hda1
sudo /sbin/grub-install /dev/hda2

```

but I just keep getting this error ```
Could not find device for /boot: Not found or not a block device.

```

HELP!

---

### Post by fluffnik on 2006-08-15
> **kbsuperstar said:**
> 
HELP!

I think
```
sudo /sbin/grub-install --root-directory=/dev/hda1 /dev/hda
```
might be what you need

---

### Post by kbsuperstar on 2006-08-15
I ended up having to do something like this

sudo grub

find /boot/grub/stage1

root (hd0,0)

setup (hd0)

And finally GRUB reinstalled, but now I can't boot up in Windows. What's the deal? Do I need to edit something in GRUB or what?

I was thinking that I had to do this, but I don't want to **** with it 'til I know for sure:

sudo grub

find /boot/grub/stage1

root (hd0,0)

setup (hd2)


Am I right?

Here's sudo fdisk -l in case that helps:

```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2860    22972918+  83  Linux
/dev/hda2   *        2861        3497     5116702+   c  W95 FAT32 (LBA)
/dev/hda3            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11549    92759310    b  W95 FAT32
/dev/sda2           11549       11694     1164681+  82  Linux swap / Solaris
/dev/sda3           11694       12188     3976087   83  Linux

```

(hda = internal HD for booting, sda = USB Mass storage device)

---

