---
title: "dual-boot issues"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Phrostay on 2006-05-17
I have a very strange Windows XP install DVD. I had a dual-boot ubuntu linux with windows XP because I require Visual Basic .NET 2003. I install ubuntu dapper drake 6.06 beta2 from a live CD ran the install but it wipped my windows XP install & now GRUB 1.5 loader always comes up. My windows XP is a HP DVD recovery disk and does not include fixmbr or fixboot tools. 

I do not have any other window machines at my house and I do not have a floppy drive or floppy disks. I have tried trinity rescue disk but it did not boot for some reason. I cannot get into recovery console with this recovery DVD and for it too install I need to remove GRUB 1.5. Is there anyway to do this from the ubuntu liveCD??? I am using a HP tc4200 tablet PC. 

Or maybe I can just virtualise and run VB.NET 2003 from linux??? My vmwareplayer. I'm not sure though because my windows XP DVD recovery disk is rather strange.

---

### Post by Borniet on 2006-05-17
No need to reinstall windows, you need to configure grub to see your windows installation, and give the possibility to boot that too. I think you can do that via the grub-install command.

---

### Post by Jagot on 2006-05-17
I was in a similar situation.  I used the FreeDos boot CD to restore the MBR which you can download here:

[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by Phrostay on 2006-05-17
Thank-you so much. The GRUB loader is now gone. phew! oh an incase anybody else is wondering I used the "fdbootcd.iso" and burnt it to disk using toast titanium on my macintosh. Once FreeDOS loaded I hit "C" for command line and entered "fdisk /mbr" note that you might have to delete the linux disk using fdisk before issuing the "fdisk /mbr" command. Hope this helps anybody else.

---

### Post by it.henrik on 2006-05-17
If you installed ubuntu after you installed win XP there should be an option at the end of the list that lets you boot XP.

---

### Post by Phrostay on 2006-05-17
yes but with the dapper drake 6.06 beta-2 live-CD the graphical installation option can be a bit deceiving, well for me anyway!

---

