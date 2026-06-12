---
title: "Ubuntu 9.04 on G3 that won't take a CD..."
date: 2009-11-16
forum: Apple Hardware Users
---

### Post by obnovas on 2009-11-16
As a disclaimer I will include the cliche "I'm a noob"...

I'm trying to salvage a whole bunch of computers for a small private school with no money. All but one of the computers are PC's. The culprit is a nice G3.  It had OS9 on it that was bogged down with a ton of software. I am loading Ubuntu on everything else with Edubuntu packages for the children.  The PCs are working great and are perfect for the kids. 
The G3 however will not take the live CD. It goes half way in. Rather than repair a lot of stuff that I don't need I disassembled and removed the HD. Placed the HD in another PC and loaded Ubuntu 9.04.  Worked great on the PC.  The mac wouldn't read the OS at all. It just gave me the flashing "finder icon and question mark".
After some reading I'm guessing it's just that the PowerPC will not read the new Ubuntu...can someone fill me in on this?  If so is there a way around this? Will an older version of Ubuntu accept Edubuntu?
Could the problem be that the mother computer is Intel and the HD is for a PPC?
Just trying to resurect the G3..any ideas?

---

### Post by linuxopjemac on 2009-11-16
You have to use a PPC-based Ubuntu CD.
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by obnovas on 2009-11-16
> **linuxopjemac said:**
> You have to use a PPC-based Ubuntu CD.
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Thanks! That makes sense. I'm guessing that I won't be able to install this using an intel PC...is that correct?

---

### Post by ZoiaGuyver on 2009-11-16
Spot on :)

The older G3/G4/G5 are all Motorola PPC processor based, it's only the newer (after 2007 i think it was) are Intel x86 based.

There are some funny "issues" sometimes with G3's and Ubuntu (not sure if they appear in 9.10 as i've not updated any of mine to it yet, working on my pc's at the mo) mainly because of the ATI onboard gfx they have, but there's a few tutorials and tips around if you get stuck.

Hopefully you can get it all installed and set up now.

Happy Ubuntu'ing :P

---

### Post by marshag63 on 2009-11-16
I have a G4 imac running 8.10 for PPC (haven't attempted 9.04 yet).  Be sure and clear PRAM (I let it chime at least four times- hold down Command, Option, P and R keys all at once) before you hold down the C key to boot from you alternate install for PPC CD.  

See following link for more instructions regarding installing ubuntu on a P3 laptop - should be pretty similar for you.

[http://ubuntuforums.org/showthread.php?t=1114297&highlight=g3+PPC+install](http://ubuntuforums.org/showthread.php?t=1114297&highlight=g3+PPC+install)


Let us know how it goes for you.  Good luck!

MarshaG.

---

### Post by obnovas on 2009-11-18
Thanks all!

I don't have another PPC computer to use as a master, and the CD drive still refuses to work. I'm thinking of just retiring the ole thing, but it just seems it would be too perfect as a "kid proof" computer. I'm thinking I might try Xubuntu or DebianEdu on it. I don't need all of the perks and pluses that 9.04/9.10 offer that would weigh it down. But I'm still in the same boat regardless.  I don't think I can boot from the USB, but will it read an external CD-Rom that I can boot from? Just a thought, I figured I would ask prior to looking for one to borrow.

---

### Post by linuxopjemac on 2009-11-18
Just download Debian Lenny PPC iso, burn it on a CD from a PC running Ubuntu. Then insert Debian into the G3 and enjoy.

Here you'll find the repository...download ppc arch
[http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)

if you prefer net installations and only want to burn 1 CD:
[http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.3/powerpc/iso-cd/debian-503-powerpc-netinst.iso)

If you can attach a CDROM it would probably also work I guess...

---

### Post by linuxopjemac on 2009-11-18
In case the CDROM(s) don't work, you might consider a network boot, also available from Debian. This requires knowledge though...

---

