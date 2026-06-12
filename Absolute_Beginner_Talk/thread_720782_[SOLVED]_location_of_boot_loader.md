---
title: "[SOLVED] location of boot loader"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Arch Parsons on 2008-03-10
Help seems to have dried up on my existing thread, so I thought it couldn't hurt to start a new one.  I'm trying to install Ubuntu on a separate partition on a drive that already has XP and Vista dual booting.  I've got so far as to where it wants to format the three Ubuntu sub partitions.  I notice, though, that is says the bootlader position is going to be hd(0).  What is this going to do with my existing boot loader for XP and Vista?

---

### Post by Duck2006 on 2008-03-10
> **Arch Parsons said:**
> Help seems to have dried up on my existing thread, so I thought it couldn't hurt to start a new one.  I'm trying to install Ubuntu on a separate partition on a drive that already has XP and Vista dual booting.  I've got so far as to where it wants to format the three Ubuntu sub partitions.  I notice, though, that is says the bootlader position is going to be hd(0).  What is this going to do with my existing boot loader for XP and Vista?

It will over write it.

---

### Post by markjensen on 2008-03-10
Clarifying, it will overwrite it, but you need it to, in order to multi-boot with Linux (Microsoft's boot loader is set up for Windows OSes).

GRUB will present you options, you can select Ubuntu or Windows (not sure if it will present both XP and Vista at GRUB, or if GRUB will pass control over to Vista's selection of XP/Vista boot).

---

### Post by Arch Parsons on 2008-03-10
Hi Mark!  Thanks for posting.  I finished the install.  After the 200 updates I found that XP was missing from the main boot menu and I have to go into Vista or Other (I'm not sure now) and then XP and Vista both are available.  Can you point me in the direction to edit this to make it the way I want it?  Thanks again for any comments!  It looks like an awesome system!

---

### Post by alphaniner on 2008-03-10
I've never used Vista, but I have a pc at work with three copies of Server 2003 installed and an Ubuntu install (don't ask).  It does the same thing.  I think the way MS OSs work, you *have to* go to MS's bootloader (the 'Vista and Other' or whatever thing you mentioned) from grub, and pick the copy of windows you want to run from there.

---

### Post by Arch Parsons on 2008-03-10
Actually it was the Vista option that took me into XP and Vista.  I think that all three OS's are nice system.  The security and stability of Linus is what attracts me the most.  Is there any filesharing software (like Azureus)  that works within Ubuntu?  Thanks for your comments!

---

### Post by VoidedCheck on 2008-03-10
Azureus works with Ubuntu.

---

### Post by jken146 on 2008-03-10
Azureus works with Ubuntu, and the best way to get it is through [medibuntu]("https://help.ubuntu.com/community/Medibuntu"), but Deluge  (in the Ubuntu repos) is better IMO.

---

### Post by Arch Parsons on 2008-03-17
Sorry to be so long getting back.  I found out how to edit Grub to change the defaults, etc. Thanks

---

