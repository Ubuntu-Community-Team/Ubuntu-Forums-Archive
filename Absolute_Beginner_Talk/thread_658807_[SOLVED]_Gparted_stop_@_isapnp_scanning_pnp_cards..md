---
title: "[SOLVED] Gparted stop @ isapnp: scanning pnp cards..."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Deadmode on 2008-01-05
I'm having some problems with gparted live cd.  Every time I use the live cd I select auto configure from the splash screen and then it acts as if it is loading and then stops at "isapnp: scanning pnp cards..." and doesn't continue any further.  I even let it sit there for about 45 minutes, but it still didn't progress.  The computer stopped thinking after a minute or 2.  I'm using an hp pavilion a335w, dual boot with Ubuntu Fiesty 7.04 and Windows XP.  My goal is to remove Windows XP partition completely since I no longer have any need for Windows.  Can anyone shed some light on this mystery? Thank you! -Deadmode

---

### Post by PapaNerd on 2008-01-17
Can't shed any light on why gparted is failing, but if I wanted to eliminate XP from a partition, I'd first wipe that partition with another utility (for example: 
[http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe)).  If gparted still fails, try using fdisk from a terminal window to create a new partition in the vacant space.

---

### Post by Deadmode on 2008-01-17
> **PapaNerd said:**
> Can't shed any light on why gparted is failing, but if I wanted to eliminate XP from a partition, I'd first wipe that partition with another utility (for example: 
[http://sourceforge.net/projects/disc-wipe](http://sourceforge.net/projects/disc-wipe)).  If gparted still fails, try using fdisk from a terminal window to create a new partition in the vacant space.

I'm sorry I didn't come back and log how I solved the problem.  What happened was that gparted and ubuntu 7.10 cd was getting confused with my video card and my onboard intel graphics (In that computer I have a Nvidia Geforce 5500 FX.) I can't quite remember how I went about it, but I scanned for what the computer was registering as my video cards with lspci and set the onboard vga graphics to run with the cd.  I used ubuntu 7.04 live cd and ran gparted from there. Got everything straightened out.  Sorry I waited so long and now I can't remember half of the stuff I did.  Thank you.

---

### Post by PapaNerd on 2008-01-18
Not a problem on the (now resolved) issue.  I was just scanning through the unanswered posts and thought a reply with a suggestion might help.

---

