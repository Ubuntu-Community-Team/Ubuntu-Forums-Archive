---
title: "Debian Package Installer Not Working From Network Share"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by darkdante on 2007-05-14
Has anyone seen this before?  I'm running Ubuntu 7.04 Feisty Fawn edition and am trying to install a Debian package that is currently stored on a remote Windows 2000 Server share.  When I right click the item and open it using the Debian Package Installer, it pops up the window but never fills out any of the information.  The box remains empty and the Install button never becomes available (it stays grayed out).

The minute I copy it to my desktop though, I'm able to install it in this manner just fine.

Is there a fix for this?

   - Ubuntu N00b born on May 11, 2007 signing off...

---

### Post by steve.horsley on 2007-05-14
Perhaps the remote filesystem isn't fully mounted. If youare using an SMB:// URL in Nautilus, it does a good but imperfect emulation of a properly mounted filesystem, but it is behaving more like an FTP client. You may well have to install smbfs and mount the share fully into the local filesystem, or jsut copy the file locally and install from there.

---

