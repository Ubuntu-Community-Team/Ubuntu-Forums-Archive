---
title: "A very bad decision"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by a_dum_bum on 2007-10-18
So here's the deal:
I had ubuntu on my laptop, but I decided that I needed the hd space for other things. So, using my partition manager, I got rid of the Linux partition on my computer and resized the windows one, so all was well in the world.
EXCEPT
I have Grub on my computer, though I thought it was part of my linux partition. Now, whenever my computer boots up, grub gets an error, and cannot continue. Fortunately I still have this ubuntu cd, which I'm using to hopefully find my Grub boot file and edit it, though I can't seem to find it. I managed to mount my windows partition so I can search through and edit things. But I can't boot to it.

Anyone got any advice? I'd really appreciate it

---

### Post by Paul820 on 2007-10-18
If you have your windows CD, load up the CD and select recovery console, then type fixmbr and fixboot to reset your MBR.

---

### Post by a_dum_bum on 2007-10-18
Unfortunately I don't have my Windows CD. I kinda am at college right now and the CD is many miles away...

---

### Post by fhqwhgads on 2007-10-18
You will need your (or even anyone else's) Windows install disk. Boot from that CD, enter recovery console, and enter the command FIXMBR. You will also want to enter the command DSKCHK to initiate a Disk Check.

After that's done you should be able to reboot without the Windows CD and get into XP - GRUB will be gone.

---

### Post by Technoviking on 2007-10-18
You could make a Windows boot CD (bootdisk.com) and copy a version fixmbr.exe on it. Microsoft use to have fixmbr.exe on their website for download.

---

### Post by stchman on 2007-10-18
> **a_dum_bum said:**
> So here's the deal:
I had ubuntu on my laptop, but I decided that I needed the hd space for other things. So, using my partition manager, I got rid of the Linux partition on my computer and resized the windows one, so all was well in the world.
EXCEPT
I have Grub on my computer, though I thought it was part of my linux partition. Now, whenever my computer boots up, grub gets an error, and cannot continue. Fortunately I still have this ubuntu cd, which I'm using to hopefully find my Grub boot file and edit it, though I can't seem to find it. I managed to mount my windows partition so I can search through and edit things. But I can't boot to it.

Anyone got any advice? I'd really appreciate it

You need a DOS boot disk with fdisk.  When you get your PC booted up in a DOS environment type the following:

```
fdisk /mbr
```

---

### Post by a_dum_bum on 2007-10-18
Thanks guys. One question: will this cost me the contents of my hard drive, or just fix the boot up problem?

---

### Post by bobplano on 2007-10-18
all your files on your windows partiton are still there, grub just doesn't like booting if there is an OS missing

---

### Post by a_dum_bum on 2007-10-18
MMMk. Thanks everyone! ubuntuforums FTW!

---

### Post by Duck2006 on 2007-10-18
> **a_dum_bum said:**
> Thanks guys. One question: will this cost me the contents of my hard drive, or just fix the boot up problem?

It will just fix your MBR on the drive.

you can also try super grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Technoviking on 2007-10-18
> **a_dum_bum said:**
> Thanks guys. One question: will this cost me the contents of my hard drive, or just fix the boot up problem?

If you partition are ok, it should just fix your boot problem.

---

