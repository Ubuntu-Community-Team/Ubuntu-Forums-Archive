---
title: "Can't See all the hardware"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by UBNUB on 2007-01-07
I decided to give Ubuntu a try from the live cd.  It seems to have recognized my graphics and sound and my two hard drives OK, as well as my network connection.

However, I cannot see my USB sticks and external drives that are plugged into a USB hub connected to my computer.  Also it is calling my hard drives USB devices (they are SATA, if that helps).

Is there something I can do to:
(1) make it understand that my hard drives are not USB devices
(2) make it see my USB devices

---

### Post by taurus on 2007-01-07
In Linux, SATA is known as /dev/sda so don't worry about it.  What's the output of this command from a terminal, Applications -> Accessories -> Terminal, after you have plugged in your external USB drives?

```
sudo fdisk -l
```

---

### Post by nite owl on 2007-01-07
I've noticed that I've had to reinstall Ubuntu everytime I connect something new i.e PCI card. Then it recognises it and it works.

---

### Post by taurus on 2007-01-07
> **nite owl said:**
> I've noticed that I've had to reinstall Ubuntu everytime I connect something new i.e PCI card. Then it recognises it and it works.

What kind of PCI card are we talking here?

---

### Post by nite owl on 2007-01-07
with rs232 connections... 2 db9s to be exact

---

### Post by UBNUB on 2007-01-07
After figuring out that the command was fdisk -<lower case L> and not fdisk -1 or fdisk -|, here are the results.  Please remember I am running off of the live CD and have not yet installed U (I'm not yet ready to jump THAT far):
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 246.4 GB, 246411933184 bytes
255 heads, 63 sectors/track, 29957 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29957   240629571    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdk: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1       48641   390708801    7  HPFS/NTFS

---

### Post by taurus on 2007-01-07
It's always a good idea to do the cut 'n paste so you don't have to type.  Use left button to cut and the middle track ball to paste.  ;) 

So, you want to access your three harddrives using ntfs filesystem.  You want to mount all of them from the LiveCD?

---

### Post by UBNUB on 2007-01-07
No, I do not want to get into the Windows drives (NFTS). From what I can tell from these fora, that is a perilous thing to attempt when your as green as I am on this Linux stuff - all sorts of corruption possibilities, I hear.

I really want to just be able to get to my flash drives/USB sticks/pen drives, plus my external USB drive.

I had tried Knoppix briefly before and I was able to see them on the desktop.   All I can see here with U is the Windows NTFS drives.

---

### Post by taurus on 2007-01-07
```
sudo mkdir /media/sdk1
sudo mount -t ntfs /dev/sdk1 /media/sdk1 -o nls=utf8,umask=0222
df -h
```

---

### Post by UBNUB on 2007-01-07
Taurus
Appreciate the help, but I do not understand the code.  What is it doing?  Do I type that into a terminal?  I am not a Linux expert and I don't speak in code.  I am confused.  What is the code going to do?  

I do NOT want to INSTALL Ubuntu yet and I surely do not want to mess up anything on my machine which is still Win XP

Thanks

---

### Post by taurus on 2007-01-07
Yes, you type those three lines into a terminal.  The first one to create a mount point so you can mount your /dev/sdk1 to it which is the second command.  The third line shows you that /dev/sdk1 has been mounted to /media/sdk1!  I thought that is what you want to do, mounting your external drive...  And if you don't want to mount it, then just forget about the commands then.

---

### Post by UBNUB on 2007-01-08
Well, thanks to all anyway.  Looks like I have to wait another tyear.  I am just too much of a newbie to understand all of this stuff.  It would have been nice, but, what the hell!:confused:

---

