---
title: "(Temporarily) disable yaboot?"
date: 2007-10-17
forum: Apple PPC Users
---

### Post by MisterRik on 2007-10-17
Due to a problem with kernel panics after installing a new, faster processor into my PowerMac G4 (Digital Audio), I'm attempting to implement the first step in fixing the problem as instructed by the vendor of the new processor: zap the PRAM & NVRAM. In the unlikely even that you've never done this before, it involves starting up the computer and holding down Command+Option+P+R until you hear the startup chime sound twice.

The problem I'm having is that this method doesn't take yaboot into account (I'm dual-booting Ubuntu & Mac OS X). Yaboot pops up right in the middle of things, interrupting the process before the second chime sounds, leaving me uncertain as to whether or not my PRAM has indeed been zapped.

Is there a way, short of completely uninstalling Ubuntu, to temporarily disable yaboot so that my machine will boot directly into Mac OS X without asking me to choose between OS X and Ubuntu?

If I must, I suppose I can uninstall Ubuntu. As I'm still in the "experimental" stage with Linux, I don't have any vital documents or other files on my Linux drive, so a complete wipe would be relatively painless.

Any advice will be most helpful, and welcome!

(Note: I'm working a 15-hour, 9:00AM to midnight, shift on Thursday the 18th, and my job doesn't involve using a computer, so it may be Friday afternoon before I can get back to this thread.)

---

### Post by pxwpxw on 2007-10-17
Try holding down the Option key, should get you a Macosx icon. 
Pobably what happened is that yaboot got installed to the first partition on the drive and zap pram just goes to that.
You need to set the boot-device in macosx so it points to the macosx partition.
See man nvram in macosx terminal.
You can also check where the yaboot bootstrap partition is from macosx using  diskutil list.

---

### Post by linear on 2007-10-19
How about just using Startup Disk to set the boot disk to Mac OS X?

---

### Post by stmiller on 2007-10-19
Yep in OS X preferences if you go to select the startup disk and simply click on the disk, it will wipe out yaboot and your computer will boot right to OS X.

To restore yaboot you'll need the alternative CD and go to rescue mode.

---

### Post by linear on 2007-10-19
> **stmiller said:**
> To restore yaboot you'll need the alternative CD and go to rescue mode.

Eh? Does the method [here]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot") not really work?

---

### Post by pxwpxw on 2007-10-19
> **linear said:**
> How about just using Startup Disk to set the boot disk to Mac OS X?

Yes easier, but nvram (or nvsetenv in linux) can also show or set boot-device for non-macosx devices (like yaboot).

---

### Post by MisterRik on 2007-10-20
Thanks, folks. I wasn't aware that using Startup Disk in the System Preferences would affect yaboot! Now I can get down to business.

---

