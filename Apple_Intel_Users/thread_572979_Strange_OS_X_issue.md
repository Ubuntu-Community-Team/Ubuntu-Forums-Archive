---
title: "Strange OS X issue"
date: 2007-10-11
forum: Apple Intel Users
---

### Post by russo.mic on 2007-10-11
So, I installed the EXT3 Driver in OS X to access my EXT 3 partition from OSX, and for the longest time, everything was working great.  All of the sudden however, my home folder is now empty in the finder!  

When I boot in to ubuntu of course, everything is fine.  in the terminal in OS X, an ls revels everything is there.  I can copy files from the EXT3 partition to the desktop of OS X through the terminal.  It seems only the Finder is screwing this up. Anybody have any ideas?  I'm  clueless.  Thanks in advance!  

Russo

---

### Post by cyberdork33 on 2007-10-11
Is there any of the normal '._' files that the finder leaves everywhere? might try removing them as they store how the finder displays things.

---

### Post by russo.mic on 2007-10-11
Nope,  Just checked, completely empty.  Good thought though.  I don't think the finder leaves that crap on the linux partition, as it runs through a different driver.

---

### Post by tgalati4 on 2007-10-11
If there are errors on the partition then OS X will mount it as read-only.  It may also change the mount partition ownership to root so you no longer have access to it.

Unmount it and run fsck.  The remount it.  Or run "Verify" using Disk Utility.

---

### Post by ronocdh on 2007-10-12
> **tgalati4 said:**
> If there are errors on the partition then OS X will mount it as read-only.  It may also change the mount partition ownership to root so you no longer have access to it.

Unmount it and run fsck.  The remount it.  Or run "Verify" using Disk Utility.
Maybe my system is somehow particularly borked, but I just tried to run Verify on my Ubuntu partition from within OS X and it wasn't a pleasant experience. I am unable to unmount the partition, which I'd suspected would be the case, because the ext3 driver I'm using for OS X just isn't very sophisticated.

Is anyone using MacFUSE ext3? I might switch to that..

To the OP, I would just try removing the ext3 driver and reinstalling it. This used to happen sometimes on my WinXP partition with the ext3 driver I had been using there.

---

