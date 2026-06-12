---
title: "USB Flash Drive Success"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Jerry N on 2007-04-29
My 2GB Sandisk Cruzer Flash Drive would not show up on the UNBUNTU desktop (Version 7.04) although I could see it with lsusb.  After a lot of fiddling around, I determined that the problem was the U3 system on the Flashdrive.  After I eliminated the U3 stuff, UBUNTU could read and write this device without difficulty.  I am a complete LINUX newby and thought I would pass this along in case it could help someone else.

Jerry

---

### Post by omkarwagh on 2007-04-30
im a newbie too. wats a U3 system?

---

### Post by Pobega on 2007-04-30
Yeah, apparently U3 support in the kernel hasn't really gotten any better, your best bet on a flash drive is really FAT16. It's the only true "universal" filesystem.

---

### Post by LaRoza on 2007-04-30
U3 was on my flash drive also, on Dapper, but Linux had no trouble reading the flash drive.

I also used it on Vista, with which U3 is not compatible, and Vista also could use the flash drive.

However, the problem came about when I ran the flash drive at school, only the U3 partition would work, and none of my work would show up.

I downloaded the U3 uninstaller but it required admin privileges to use. I brought it home and it would not work on Vista!

So I had to find someone who had XP who would let me have admin privileges. U3 is a pain.

---

### Post by Jerry N on 2007-04-30
U3 is a program system that allows programs to run from the flashdrive.  In theory, this makes the programs portable - in practice the system seems to be a bit "iffy".  You can read more about it at [www.u3.com](www.u3.com).

Jerry

---

### Post by LaRoza on 2007-04-30
PortableApps.com is the place to go for portable apps.

---

### Post by jb6000 on 2007-04-30
I too have a Sandisk Cruzer but did not experience the problem you are having... my problem is trying to eject the Sandisk Cruzer. I simply wouldn't let me. I need to reboot by laptop befor I am able to pull my thumb drive.

---

### Post by RSingh on 2007-05-05
WORKS FOR ME....:guitar: 

Here is the fix :

I had the same problem of mounting Sandisk Cruzer Micro (2GB).  Initially I thought the problem is with U3 software......however, it is not so.  Just disable the security  feature in U3 (the password system) by mounting the drive in Windows.  It will work fine and mount without any problems in linux.  Remember, once the security features are enabled, it will need windows computer to mount it.  It can not be mounted in linux if this feature is on.

---

### Post by crmccreary on 2007-05-06
See [http://ubuntuforums.org/showpost.php?p=2580033&postcount=27]("http://ubuntuforums.org/showpost.php?p=2580033&postcount=27"), 
 worked for me although I don't know why or for how long.

---

### Post by catkeys on 2007-07-17
I'm a Feisty Fawn newbie (and a USB flash drive newbie).  Help!

Under Ubuntu, I downloaded Grisoft's free virus software for XP (I have a dual-boot Linux - XP system, & need virus protection under XP))

On Ubuntu, I then plug in my Sandisk Cruzer 4 G USB drive.  It displays politely in the the File Browser tree as 'disk'.  Although U3 is on the drive, it doesn't seem to  activate or cause problems.  I can copy my file to the drive without a problem.

But what is the proper way to remove the drive from the USB port?  Right-click on 'disk', and choose 'Eject'?  Various Googling's mention an icon somewhere on the screen, but I can't find any icon related to the drive.

When I do eject, and later try to run the file under XP, I get a error message: 'some files are corrupted'.  I don't know if I corrupted the file by removing the drive incorrectly, or if there's a different problem.    I definitely need to understand how to remove the drive!

Thanks!

---

