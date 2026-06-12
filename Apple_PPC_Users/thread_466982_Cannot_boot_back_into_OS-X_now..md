---
title: "Cannot boot back into OS-X now."
date: 2007-06-07
forum: Apple PPC Users
---

### Post by maxxum on 2007-06-07
I have an old-ish powermac G4. I have been trying to get xubuntu (6.10) to work as a dual boot with OS-X. It used to work fine when I had a CRT monitor. After I got an LCD (thread [_here_]("http://ubuntuforums.org/showthread.php?t=464527")), I had problems getting xubuntu to display properly but my OS-X used to work perfectly. 
During the process of trying to get the X-server to work when in linux, I had to do quite a few hard reboots to the machine (since I couldn't see anything on the screen) and once I even reset the system clock on the motherboard based on some advice on the forum.
Well at some point during this process I lost the ability to boot into OS-X. I have installation disks of OS-9 (panther) that came with this machine, but not OS-X (which I will have to get from the system admin who installed it for me). 
I was wondering if I can do any repairs myself before taking it to the system admin. Also I had a bunch of programs installed in there so I do not want to lose that installation. 
When I boot, it just sits at the grey screen with an apple logo on it and a spinning wheel below. It seems that I might never get ubuntu ppc to work with my LCD so I would just like to get the OS-X to work. 
Thanks!

---

### Post by ssam on 2007-06-07
try holding down apple+V after you have selected to boot mac os x.

this should show you all the startup messages. there might be a clue as to where it is getting stuck.

---

### Post by maxxum on 2007-06-07
Thanks. I did the verbose boot as you said and it said i mounted the file system and soon after it seems to get in an infinite loop printing this line repeatedly forever...

IOATABLOCKStorageDriver::sCompleteZeroBlocktransfer-WARNING, completing a zero block transfer

It seems that it is something related to the I/O from the ATA drive. Any way to reslve this from OS 9 disks?

---

### Post by maxxum on 2007-06-07
I want to post an update that I have fixed that issue. Some googling led me to a link where some good man had posted what worked for him and I saved myself the purchase of some disk utility. Let me post it here in case someone else comes along looking for this.

When booting, hold down Apple+S as soon as you hear the startup chime (if yours is muted, like mine was, just guess, press them as soon as the caps lock key light goes off) and release them when the grey screen with apple comes up. This lets you login as a single user. Once in the command prompt type: 
fsck_hfs -r /dev/disk0s9

and it will run with messages about what it is finding and fixing. You may have to run it more than once as it tries to fix everything in three iterations which may not be sufficient. Note that disk0s9 was the location of the OS root directory in my case. It may be different in your case. (you may find it by typing df on the command prompt and pressing enter).

_Now the next problem:_
Now that my OS-X is fixed I need to get the 1920x1200 resolution. The ATI Rage 128 with 16MB graphics officially supports this resolution but only on analog LCD monitors. It supports 1600x1050 on digital monitors like these. However currently it only shows 1280x1024 to me. Is there some sort of xorg.conf for OS-X?

UPDATE: I figured out that the DVI connection does not give the optimal resolution. As soon as I connected with the VGA cable, it gave me the max resolution by default. I thought maybe that was why it wasn't working well in ubuntu. Hpwever I lost the ability to dual boot when I replaced the DVI with VGA because now when I press the option key while booting the machine, I cannot see the Mac and Linux options, the screen just goes into sleep mode. After a while when I release the key, OS-X boots. Well, I guess one cannot have everything. :(

---

### Post by cv_zero on 2007-07-12
So I've been dying to figure out how to boot in verbose mode, I've read a million posts, this thread gets pretty close, but still, no one actually has answered, How do you boot in verbose mode?

---

