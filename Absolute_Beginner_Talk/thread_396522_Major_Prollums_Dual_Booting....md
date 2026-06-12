---
title: "Major Prollums Dual Booting..."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by qrprat77 on 2007-03-29
Hi!
I have an older system 2001 year, Compaq Presario 5000, Athlon XP processor, 80Gig Maxtor IDE drive, and am having what appears to be many problems...
The goal is to have a dual boot system,
Windows XP (original OS)
and Ubuntu 6.10
First,
I did copy most of the important things off the harddrive before I fooled around with installing it, but if possible, I'd rather restore XP and check again
I ran the Edgy installation, and had no problems creating a new partition and what not, as a matter of fact I was very pleased with the whole process.

Then I restarted the computer and I get the classic "Loading grub 1.5" and then "Error 17"
The system freezes.

My research suggests I need to change something about the way grub calls partitions, so I put in my trusty ubuntu installation cd, hoping to correct the problem.

Now, when I hit the run Ubuntu option from the startup menu, the system will not load.  It seems to load the kernel, but the gui is gone, there is no command line, and no blinking cursor.  The CD drive stops running, and everything just quits.

When I tried to put my compaq system recovery disk in, it won't load either.

Help!

---

### Post by dbbolton on 2007-03-29
first off, i think you might need a new cd.

once you can boot a livecd, give this a go:

> **bulldog said:**
> Just reinstall grub from the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```This will get you a grub> prompt 
```
find /boot/grub/stage1
```This will return a location which you have to use in the next command. 
```
root (hd?,?)
```Next enter the command to install grub to the mbr
```
setup (hd0)
```Exit the grub shell
```
quit
```Now Grub will be installed to the mbr.

---

### Post by atosecond on 2007-03-30
I recall having a similar problem, what i ended up doing was putting an xp installation cd in the drive running fixmbr from the recovery console. rebooting putting a live cd in and reinstalling grub.

---

### Post by qrprat77 on 2007-03-30
My shift  is done now I can start my weekend!!

Ok,
I tried the reinstallation of grub thing, and that didn't work.  
There did seem to be a problem with the installation cd.  I'd used it to install Ubuntu on several computers, with no prollums, but I guess I musta scratched it or something...
New disk works great!

Time for some more research...

---

### Post by qrprat77 on 2007-04-06
OK!
So here's the deal...
I figured out how to access and successfully copied the one file from my harddisk I just couldn't live without...
So,
Keeping the machine dual boot isn't as important to me right now.

I still want to make it dual though...

---

