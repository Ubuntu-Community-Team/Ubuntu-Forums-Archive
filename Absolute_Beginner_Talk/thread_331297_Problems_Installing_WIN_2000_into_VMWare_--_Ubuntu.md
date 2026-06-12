---
title: "Problems Installing WIN 2000 into VMWare -- Ubuntu 6.10"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-04
I have set up a virtual machine for WIN 2000. However I cannot install the operating system.

The CD drive will not boot up for WIN 2000 for installation. I have looked at the help article "Configuring a CD-ROM" and even with the suggested changes (changing CD-ROM from local to client), nothing occurs.

This is the error message I receive:
-----------------------
No bootable CD, floppy or hard disk was detected.
To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button.
-----------------------

I am uploading a screen shot so you can see what I see directly. (Being a noobie in Linux it saved the screenshot as .php -- I have no clue how this compresses the file -- so if the pic is too large, let me know & I won't do this again)

What do I need to do in order to get WIN 2000 installed?

---

### Post by gilbertr on 2007-01-04
This may sound a silly question ....but are you sure the CD is bootable ?  Does it boot on an actual PC ?

---

### Post by chaplanger on 2007-01-04
To answer the question:
Yes, the CD is bootable -- it is a "genuine" M$ 2000 professional (full version).  It does boot for installation on a PC, but not recognized within VMWare.

---

### Post by Bachstelze on 2007-01-04
Are you sure VMWare is properly configured to use the CD drive ? Also, you have VMware Server, not VMware Player, right ?

---

### Post by chaplanger on 2007-01-04
> **HymnToLife said:**
> Are you sure VMWare is properly configured to use the CD drive ? Also, you have VMware Server, not VMware Player, right ?

It is possible that VMWare is not properly configured to use the CD drive -- I looked at the help article (from within VMWare) "Configuring a CD-ROM" and even with the suggested changes (changing CD-ROM from local to client), nothing occurs.  (Though, as this process fails time and again I begin to wonder if there is something I am missing in this process.)

Yes, we are looking at VMWare Server (not player).  VMWare Server set right up.  It's just adding the actual OS that is getting a bit 'hairy' 

FYI -- Running Ubuntu 6.10 (Edgy Eft)
I set up my virtual machine for 10GB HD space and running with 256MB of RAM.

---

### Post by chaplanger on 2007-01-04
I have now attempted to use a created ISO image of the WIN 2000 CD (changing the CD Rom settings to ISO image and the correct file and location) -- this will not begin the process either.
The error message I receive is just as before and the ISO image is not recognized as bootable either:
--------------------------------------------
CLIENT MAC ADDR:  00 0C 29 85 34 91 GUID: 564DACD0-47CA-3355-D621-5581A1853491 
PXE-E53:  No boot filename received

PXE-M0F:  Exiting Intel PXE ROM.
Operating System not found
------------------------------------------

Any Ideas out there?

---

### Post by wrycatcher on 2007-01-29
I too have encountered this problem.  I'm scouring the net (and these forums) for a solution.  I have heard someone saying I have to specifically enable the CD-rom in the VM's bios.   I won't be able to test the theory until tonight, though.

---

### Post by wrycatcher on 2007-01-29
Hmm...seems that's the likely culprit...boot order in the VM bios:  [http://www.faqts.com/knowledge_base/view.phtml/aid/27092](http://www.faqts.com/knowledge_base/view.phtml/aid/27092)

---

### Post by wrycatcher on 2007-01-29
I keep answering myself, but wanted my discoveries to benefit others facing the same dilemnas.  The other thing I have discovered is that some versions of older OS's (even as recent as Win98) might not have "bootable" CDs.  In this case, it doesn't matter if you change the BIOS or not, you'll need a diskette (or a different bootable CD) to boot into an OS of some sort.   I recommend looking at [www.bootdisk.com](www.bootdisk.com) for help creating bootable media.  I also found Smart Boot Manager to be a very handy bootable disk image when messing around with OS CD's that are not bootable.  Also handy for cases when the machine BIOS doesn't support booting from CD.

Once you have a physical diskette (or a flat diskette image file) you can configure your VM to boot to that location.  Then you should be able to continue with the CD's setup application.

---

