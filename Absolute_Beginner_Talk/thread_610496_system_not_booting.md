---
title: "system not booting"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by perdition79 on 2007-11-12
I'm a new Ubuntu user, and I'm having a bit of trouble getting my computer to restart.  It froze while playing Unreal Tournament 2004, so I had to shut down and restart.  Instead of giving me a list of boot options, the GRUB loader just says "error 21" and I have no idea what to do.  Has anyone else encountered this problem, and have any advice?  Thanks in advance.

---

### Post by bulldog on 2007-11-12
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Check your hdd,I think it's broken.

---

### Post by Sorivenul on 2007-11-12
GRUB error 21 is cited as an "Unknown boot failure".  I don't know much more than that.  It may not hurt to reinstall GRUB, just as a thought.

---

### Post by perdition79 on 2007-11-12
Thanks!!  I'll get started on that route.  I'm running Ubuntu off a 60-gig USB drive, and the BIOS is really easy to tinker with.

---

### Post by perdition79 on 2007-11-12
> **bulldog said:**
> 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Check your hdd,I think it's broken.

It worked.  Something was messed up in my BIOS, it now sees my USB drive as a USB-ZIP drive.  Hey, it works, so I'm not questioning it.  Thanks for the help.

---

### Post by bulldog on 2007-11-12
> **perdition79 said:**
> It worked.  Something was messed up in my BIOS, it now sees my USB drive as a USB-ZIP drive.  Hey, it works, so I'm not questioning it.  Thanks for the help.

I would :)
Just because playing a game will mess up the BIOS.................I would wondering why.

---

### Post by dezoete on 2007-11-12
Hi
I have a simillar (different?) problem::KS

I had Ubuntu installed, (7-10), no problems. But then I had a major computer breakdown, and had to install everything from start.
Installed my windows XP, with all  the programs I use there. (including AVG  antivirus and Windows firewall). Then took the same installation disk with which I installed Ubuntu the first time, and re-installed Ubuntu. It did the installation OK. on a slave disk , 50% of disk space (115 G)
I re-started my computer- and it re-started in windows ONLY!
I tried again, but only can access windows.... What to do?:(

---

### Post by bulldog on 2007-11-12
> **dezoete said:**
> Hi
I have a simillar (different?) problem::KS

I had Ubuntu installed, (7-10), no problems. But then I had a major computer breakdown, and had to install everything from start.
Installed my windows XP, with all  the programs I use there. (including AVG  antivirus and Windows firewall). Then took the same installation disk with which I installed Ubuntu the first time, and re-installed Ubuntu. It did the installation OK. on a slave disk , 50% of disk space (115 G)
I re-started my computer- and it re-started in windows ONLY!
I tried again, but only can access windows.... What to do?:(

Two hdd's?
Set in the BIOS to boot from the other one and see what happens.
You should at least get grub,maybe it won't boot,but that is to be corrected in menu.lst

---

### Post by alienexplorers on 2007-11-12
Try using the super grub disk to see if it fixes your problem.

---

### Post by dezoete on 2007-11-12
Thanks Bulldog! 

It seems I have a problem with the Bios.... The Bios boot disk sequence shows only one hard disk, so I'll have to solve that... Thanks for the reply

---

