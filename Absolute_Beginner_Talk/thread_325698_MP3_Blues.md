---
title: "MP3 Blues"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by canfield on 2006-12-26
Hello Hello

I wish to download music onto my Sandisk sansa 2 gig.  Can anyone help a newbe like me.  PS Ubuntu is the first Linux system I have found to load and work well for me.  I hope the forums work as well.

Paul

---

### Post by qalimas on 2006-12-26
Plug it into your computer and turn it on, then an icon should appear on your desktop for it, just copy the music right over I suppose.  That's how it works for my brother's.

---

### Post by canfield on 2006-12-26
I only wished it would be that easy.  This does not work, any other ideas would be great.  

Paul

---

### Post by Sef on 2006-12-26
What operating system are you using?

---

### Post by norman_ on 2006-12-26
Please give more details. Unfortunately, I don't think you can expect us to solve your problem if you only describe it as "it doesn't work"

When you plug it and turn the device on, does the drive appear on the desktop?

---

### Post by canfield on 2006-12-26
The operating system is Ubuntu 6.10.  When I plug the mp3 player into the usb the player turns on and shows connected between device and computer.  Nothing shows up on screen and when  I look under system/ preferences/ removable drives and media nothing shows up.

Paul

---

### Post by Azakus on 2006-12-26
Run this command and see if you see your Sansa player in there
```
lsusb
```
If you do, then Linux does see your player, it just hasn't automounted it correctly.
Then run ```
sudo fdisk -l
```
and post the output here.

---

### Post by canfield on 2006-12-26
Thanks but I need to find and read the manuel because run does not compute.  In Win I can do it, but not here yet.  Again Thanks

Paul

---

### Post by norman_ on 2006-12-26
What he meant by "Run" is not like the windows run. You have to go in the applications menu, accessories, and pick console. When you open that console, type in the commands he told you to and post the output.

---

### Post by Azakus on 2006-12-26
> **norman_ said:**
> What he meant by "Run" is not like the windows run. You have to go in the applications menu, accessories, and pick console. When you open that console, type in the commands he told you to and post the output.

Yeah. That's what I meant. Sorry if that was a little over your head.

---

### Post by canfield on 2006-12-26
This is what I got

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9648    77497528+  83  Linux
/dev/hda2            9649        9729      650632+   5  Extended
/dev/hda5            9649        9729      650601   82  Linux swap / Solaris
paul@opy:~$ 


Does this help

---

### Post by koholint1000 on 2006-12-26
Right; that means that your ubuntu doesnt register it as a Hard Disk yet.

What's the output of lsusb?


(Even, does it show up in System > Administration > Disks ? > Device Manager ? )

---

### Post by canfield on 2006-12-26
paul@opy:~$ lsusb
Bus 002 Device 006: ID 0781:7420 SanDisk Corp. 
Bus 002 Device 002: ID 0bda:0111 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
paul@opy:~$ 

I think this is what you mean

paul

---

### Post by koholint1000 on 2006-12-26
Right; im assuming this is a memory card (correct me if im wrong). I had a similar problem with my SD card reader. I fixed it in the most peculiar way: I did a multitude of things, 1) Tried the reader in all the USB ports (not applicable if it's an internal reader), 2) Alternated between having the little switch n the card either way. Try re-inserting it. Try having it plugged in at start up (in all configurations).

I don't know the h4x0r 1337 way of doing it; I only know n00b ways. Hope this helps you.

(P.S. try this: (use vfat if the disk is Fat filesystem, ext3 if it is linux, or NTFS if its ntfs (unlikely) )

```
cd /
mkdir /mnt/sda6
mkdir /media/sd-card
mount -t vfat sda3 /media/sd-card (or /mnt/sda6)
```

It probably wont work, but give it  a shot. perhaps try each with sudo in front. Just trying to help :D

---

