---
title: "Booting The Xubuntu Installer Cd"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by pmcary on 2006-12-06
I have been trying to install Xubuntu on my old windows 95 computer. (it is 100% formated now unfortunatly).

I figure out how to work it just fine on my other computer that was already running windows, but i'm not quite sure what i should do to get Ms Dos to run the install/setup file.

If anyone has any experience here, and could lend a helping hand, i would be grateful.

ty for your help
~cheers.

---

### Post by Mimsy on 2006-12-06
Hm... I have no recent experience with Win95 (to be precise, I haven't used it since 1998 ) but my instinctual response is to ask if you can boot the live CD, or the alternate CD if the live one doesn't work? If you can boot off of either of those, you can install from there.

If you want to dual boot, I strongly recommend looking up  few articles amd howtos before you start creating partitions. Other forumites will be able to be of more help in that department.

Good luck!

/Mimsy

---

### Post by pmcary on 2006-12-06
yeah...i would love to just boot off the live cd, but it starts up with my boot disk in A:\...

then i type in R:\ (this is because R is my cd drive)
from there, im not sure what to type...for windows, i believe it is setup.exe, but this does not seem to work for xubuntu.

---

### Post by kakalaky on 2006-12-06
Go into your bios setup and set it to boot the cd drive before the hd.

---

### Post by Sef on 2006-12-06
>  	yeah...i would love to just boot off the live cd, but it starts up with my boot disk in A:\...

You need to go into your BIOS and change it to boot from the CD.  It could be too that because your computer is so old that you don't have that option.

To get into the BIOS, you need to press, while starting up, one of the following (usually):  esc, del, F2, F12, or sometimes another key.  Upon start up, your computer will tell you what to push to get into the BIOS.

Live CD Tutorial by [Psychocats]("http://www.psychocats.net/ubuntu/installing")

Getting into the BIOS and Changing it in the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/p1.htm").

Questions for you:

1) How much ram does your computer have?  Xubuntu can do with 64 mb ram, but really needs 128 mb ram.   If you have less than 64 mbs ram, there are other distros that will work on your computer.

2) How fast is your processor?

---

### Post by pmcary on 2006-12-06
Ok...i'm not sure why it works now...but in BIOS, it was set to boot from CD-ROM primarily.

So when I try and boot it from the boot disk, it loads as usual...

> Floppy A: Installed




Insert bootable media in the appropriate drive
Here, i just press enter
> ISOLINUX 3.11 Debian-2006-03-16 isolinux:
Cannot boot from this CD. Please use CD2 or try a BIOS update

in bios it also notes:
> BASE MEMORY: 640 KB
Extended MEMORY: 31744 KB
RESERVED MEMORY: NONE
CPU SPEED: 166 MHz

perhaps my computer is too slow to run this? I don't see why it wouldn't at least try and setup...then run really slow once that happens.

---

### Post by Mimsy on 2006-12-06
"Cannot boot from this cd" to me means that something is wrong with the CD itself. Did you burn it at the slowest possible speed? What do you get if you check the cd for errors?

/Mimsy

---

### Post by pmcary on 2006-12-06
> **Mimsy said:**
> "Cannot boot from this cd" to me means that something is wrong with the CD itself. Did you burn it at the slowest possible speed? What do you get if you check the cd for errors?

/Mimsy
I was actually just running the cd in live mode on my regular computer when i was posting my most recent replies to test it, and it seemed to work flawlessly. 
I don't see why the cd would be flawed if it works for one of my computers.

---

### Post by Sef on 2006-12-06
> I don't see why the cd would be flawed if it works for one of my computers.

So your LIve CD works on one computer but not this one? 

> BASE MEMORY: 640 KB
Extended MEMORY: 31744 KB
RESERVED MEMORY: NONE
CPU SPEED: 166 MHz

Your computer doesn't have enough memory for xubuntu.  I would recommend trying [delilinux]("http://delili.lens.hl-users.com/") first and then [vector linux]("http://vectorlinux.com/").  They are both made for low memory systems.

---

### Post by pmcary on 2006-12-06
> **Sef said:**
> So your LIve CD works on one computer but not this one? 

that is correct.



[QUOTE=Your computer doesn't have enough memory for xubuntu.  I would recommend trying [delilinux]("http://delili.lens.hl-users.com/") first and then [vector linux]("http://vectorlinux.com/").  They are both made for low memory systems.[/QUOTE]

Ill give it a shot, thnx for the help...any reason why it the computer wouldn't even try it though?

---

### Post by Mimsy on 2006-12-06
Seconded. I hadn't seen your system specs when I made my previous post, or I would have suggested a ligter distro straight away. Damn Small Linux comes to mind...

Sef is a smart guy though... go with his advice for now, it usually helps. :)

/Mimsy

---

