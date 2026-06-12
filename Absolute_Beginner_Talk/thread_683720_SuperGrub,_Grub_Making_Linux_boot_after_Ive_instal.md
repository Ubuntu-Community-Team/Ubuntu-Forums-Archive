---
title: "SuperGrub, Grub Making Linux boot after Ive installed Vista!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by nilsh on 2008-01-31
Hello! 

I am posting here, because I am a complete noob when it comes to linux, but I am hoping someone can help me :)

My computer is a Dell laptop 2.20 Ghz M1330. It was installed with vista and some other pauxrtitions on it (Media Direct and Recovery).

I wanted to install linux, so I loaded up the ISO Gparted cd and began destroying the recovery and mediadirect partitions. I then installed linux, having one swap partition, one ext3 partition and one large one for vista os. But since I managed to shut down the computer half way in the partitionmaking, so I had to start over, and destroy the Vista partition too :)

So then I had ext3, swap and 223gb for ntfs.

I installed linux, happily over the result, and wanted to re-install vista. This worked somewhat (errors with updating) but the GRUB boot loader is gone!  I saw some posts about the Super Grub CD, and made an ISO of it. But it didnt make much sense to me.

So my question is, how can I boot up linux now? I cant boot it, and cant get GRUB to load either. It seems that Vista has taken complete control of my system!

HALP HALP HALP!

Thanks in advance,

- a complete noob.

---

### Post by broekskw on 2008-01-31
hi nilsh, did you take a look at this site, it explains how to recover or boot into diff systems using the SUPERGRUB disc

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted)

i just made one disc last night for save keeps

hope this helps:lolflag:

---

### Post by jaytek13 on 2008-01-31
As far as just simply restoring it, here is a tutorial:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It just requires you have the ubuntu livecd.

---

### Post by nilsh on 2008-01-31
Well, I did follow that last how-to, and now I get to log into Linux!

But that is all! I can't log on to Vista anymore, its not even in the grub menu!

What to do ?

---

### Post by NorthernPaladin on 2008-01-31
[http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/](http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/) I tried that and I could boot into linux, but cant use linux now because it does not recognize my keyboard

---

### Post by dstew on 2008-01-31
You can edit the grub menu file and add an entry to boot Vista. You can use the gedit program from your Ubuntu system:```
gksudo gedit /boot/grub/menu.lst
```At the bottom, below the ### END DEBIAN AUTOMAGIC KERNELS LIST line, add these lines:```
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```First check the menu.lst entries to see if the Ubuntu system is given the root (hd0,0). If so, use root (hd1,0) in the Vista entry. After editing the file, save it, and reboot.

---

### Post by nilsh on 2008-01-31
> **dstew said:**
> You can edit the grub menu file and add an entry to boot Vista. You can use the gedit program from your Ubuntu system:```
gksudo gedit /boot/grub/menu.lst
```At the bottom, below the ### END DEBIAN AUTOMAGIC KERNELS LIST line, add these lines:```
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```First check the menu.lst entries to see if the Ubuntu system is given the root (hd0,0). If so, use root (hd1,0) in the Vista entry. After editing the file, save it, and reboot.

Thanks! Ill try that :)

But my Ubuntu is currently on (hd0,5) - What do I give my Vista? (hd1,5) ?

Thanks in advance

---

### Post by dstew on 2008-01-31
First do **sudo fdisk -l** so we can see all your partitions. Then we will be able to figure out what the root for Vista should be.

---

### Post by Michl on 2008-01-31
Had a similar problem and here is the upshot

[http://ubuntuforums.org/showthread.php?t=526375](http://ubuntuforums.org/showthread.php?t=526375)

The thread gives you various things you can do but
the upshot was I had to reinstall everything.

---

### Post by nilsh on 2008-02-01
My Vista partition is on sda2, while my linux is on sda5.

Don't know why it's so messed up :)

---

### Post by nilsh on 2008-02-01
When I try (hd0,2) it says:

Error 22: No such partition

If i try anything else, it's error 21, no such disk

EDIT: Nevermind :D

hda2 = 0,1 :D

Problem solved, it worked now!


Thank you so much for helping me, I really appriciate it!

---

### Post by jaytek13 on 2008-02-01
> **nilsh said:**
> When I try (hd0,2) it says:

Error 22: No such partition

If i try anything else, it's error 21, no such disk

EDIT: Nevermind :D

hda2 = 0,1 :D

Problem solved, it worked now!

I was just gonna say that... Anyways, for the future, the numbers in (hd0,0) correspond to the drive # and the partition #. So, the first drive on your computer will always be 0. If you only have one drive you would get an error when trying to enter (hd1,2), for instance, because in this example the 1 would be drive #2 since drive #1 is 0.

---

