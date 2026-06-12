---
title: "Can't Burn Cds in Virtual Box"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-08-25
I have vbox running on Ubuntu Fiesty, on a Lenovo Z60M machine.  Here is a product link:
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U)


Virtualbox runs fine, and it sees my cdrom drive and will read from it, but it doesn't seen the drive as a burner.  I installed Nero and Nero doesn't see it either, just to confirm.  From My Computer, under XP in Vbox, it shows the cdrom drive as a "cd drive" when in fact it is a DVD-rom writer.

I cannot get Nero to burn anything or iTunes to burn either.  Any ideas on this?

---

### Post by uclalinux on 2007-08-25
just use K3B to make cd's 

and is your fstab file correct, 

post your fstab file 

from terminal type,  gedit /etc/fstab

---

### Post by nonewmsgs on 2007-08-25
are you the same fellow asking about the amorak/banshee/itunes?  (not that there's anything wrong with that just making sure i dont have to point someone else to this post if it works)

ok virtualbox (at least the one on the site not sure about repositories) offers a shared folder , but i dont know if that will fix your problem (since it's most likely protected).

let me know if that does happen to solve it so i know if i have to look deeper into vb.

---

### Post by kc5hwb on 2007-08-26
uclalinux:
I already use K3B for burning on Ubuntu, my problem is with Vbox seeing my burner.  I can burn through Ubuntu just fine.

nonewmsgs:
Yes, that amaroK/Banshee thread is mine also.  But I haven't been able to get the shared folder in vbox to work, where is it?  I remember reading about it when I first install vbox a few months back, but I couldn't get it to work and I haven't tried since.

---

### Post by stevebakerj on 2007-08-26
> **kc5hwb said:**
> I have vbox running on Ubuntu Fiesty, on a Lenovo Z60M machine.  Here is a product link:
[http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U](http://www-307.ibm.com/pc/support/site.wss/quickPath.do?quickPathEntry=2529R5U)


Virtualbox runs fine, and it sees my cdrom drive and will read from it, but it doesn't seen the drive as a burner.  I installed Nero and Nero doesn't see it either, just to confirm.  From My Computer, under XP in Vbox, it shows the cdrom drive as a "cd drive" when in fact it is a DVD-rom writer.

I cannot get Nero to burn anything or iTunes to burn either.  Any ideas on this?

How does VirtualBox see the drive in its 'settings' for the guest OS?

---

### Post by kc5hwb on 2007-08-26
In the details of the VB folder, it shows: 

CD/DVD-ROM
Host Drive
HL-DT-ST DVDRAM GMA-4082N (/dev/scd0)
 
In windows, it just shows "standard cd-rom drive"

---

### Post by schorsch on 2007-08-26
I have fiddled around with that, too. In he FAQ it is told that experimental support for ATAPI devices is available since 2006 to support burning devices. But mine is a SCSI CD-RW in my laptop just like yours (/dev/scd0) and not an ATAPI device ... thus there may be the problem ....

---

### Post by kc5hwb on 2007-08-26
I don't think mine is SCSI, but I do think it is SATA, and I believe Linux reads SATA like a SCSI device.

---

