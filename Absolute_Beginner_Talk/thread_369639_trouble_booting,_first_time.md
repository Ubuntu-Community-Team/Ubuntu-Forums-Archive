---
title: "trouble booting, first time"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Chris_C on 2007-02-24
Hi. I'm trying Ubuntu for the first time. I can't get it to boot my computer. I have a Dell Optiplex running XP. Even though the Ubuntu CD I burned is in the drive it still boots up XP. I'm pretty sure it burned correctly. At start up I checked the boot menu, which gives me three choices: 1. Diskette Drive, 2. Hard-Disk Drive C:, and 3. CD-ROM device (not installed). I'm guessing then that the CD-ROM device should be installed, but I don't know how to change it. Any suggestions on what I can try to make this work? Thanks.
Chris

---

### Post by halitech on 2007-02-24
if your system doesn't think it has the cd rom installed, then you either have a dead cd rom or it's diabled in the BIOS. Either way, without a working, seen cdrom, you can't install from the cd.

when you are in XP, does your cd rom work?

---

### Post by irish_flu on 2007-02-24
Is the CD drive internal, or is it USB (external)?

---

### Post by ViRMiN on 2007-02-24
I had this on an OptiPlex machine last week; turned out to be the connection of the lead to the CD drive from the motherboard... open it up and check it's secure on the drive.

---

### Post by Chris_C on 2007-02-24
It's an internal drive, shows up as the D drive, and it works fine, I can download Firefox and so on from the CD. - Chris

---

### Post by halitech on 2007-02-24
I've got one home but I can't remember the sequence right now but basically you need to set it to boot from the cd rom in the BIOS

---

### Post by irish_flu on 2007-02-24
OK.  If the drive works fine in Windows, perhaps we're putting too much emphasis on the "not installed" thing.

Just to be clear, did you change the boot order in the BIOS so that it tries the CD before it tries the hard drive?

---

### Post by Chris_C on 2007-02-24
I don't see how to change the order. I either check or uncheck each option. I tried checking only the CD-ROM option, but it was unable to boot up.

---

### Post by Maestro23 on 2007-02-24
Chris_C, how did you burn the image?  What program and what speed?

I just googled your system.  If you have the options set right, it will boot from the CD drive if the CD has an OS on it.  If not, it will go to the next device in the boot order.

---

### Post by Chris_C on 2007-02-24
I burned it using the Infra Recorder as recommended. I don't know the speed. The files display correctly according to the sample given on the Ubuntu website. How do I set the boot up options, other than what I already tried? I didn't see any option besides checking/unchecking the three choices available.

---

### Post by Maestro23 on 2007-02-24
> **Chris_C said:**
> I burned it using the Infra Recorder as recommended. I don't know the speed. The files display correctly according to the sample given on the Ubuntu website. How do I set the boot up options, other than what I already tried? I didn't see any option besides checking/unchecking the three choices available.

I found this site, might not be your exact model, but I'm sure the process is the same on all Dell's in that line.  

[http://tomcat.yc.edu/servman/Desktops/GX400_UG/ch2.htm](http://tomcat.yc.edu/servman/Desktops/GX400_UG/ch2.htm)

I would try and use a different burning program and burn at a 4x is possible.  Also, you might want to check the tech section for your model at Dell's site.

Good luck.

---

### Post by irish_flu on 2007-02-24
Hey Chris,

Which model of Optiplex do you have?  Dell has been making this line for many many years (I think the first Optiplex I used was a 75MHz Pentium with 16MB of RAM) and the specs vary widely.

---

### Post by Chris_C on 2007-02-24
HI, it's an Optiplex GX240, Pentium 4, 1.8 GHz, 512 MB of RAM. About 5 years old.

---

### Post by Maestro23 on 2007-02-24
> **Chris_C said:**
> HI, it's an Optiplex GX240, Pentium 4, 1.8 GHz, 512 MB of RAM. About 5 years old.

Any progress on the boot issue?

---

### Post by Chris_C on 2007-02-24
Yes. I found and followed directions online for the Optiplex GX240. It now boots up from the disk first. Thanks for leading me to it. New question, and new problem. 

Question: can you have both operating systems saved on the hard drive and choose between them, or do you have to dedicate yourself to one or the other? (Am I supposed to start a new thread?) Since at start up it goes through a hierarchy of drives to boot up from, I didn't see how you could set up the choice on the hard drive to choose between them. 

New problem: as Ubuntu is booting up and goes through it's check list, it ends on a window which says: "Out of range signal. Cannot display this video mode. Change to 1600x1200 @60hz". At that point the computer is stuck on that window and won't do anything else. So I've restarted the computer back in XP and checked the screen resolution, and it is set at exactly that, 1600x1200 @60hz.  What can I do about this now?

---

### Post by andrew.46 on 2007-04-27
Hi Chris,

 Saw a GX240 mentioned:

> **Chris_C said:**
> HI, it's an Optiplex GX240, Pentium 4, 1.8 GHz, 512 MB of RAM. About 5 years old.

 I run a GX270: great machines!! Probably by now you have found the[ Dell Support for the GX240]("http://support.dell.com/support/edocs/systems/opgx240/en/ug/index.htm")?

           All the best,

                 Andrew

---

