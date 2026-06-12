---
title: "installing on MacBook HELP!"
date: 2008-07-16
forum: Apple Hardware Users
---

### Post by BaddaBlaiyke on 2008-07-16
so basically, im trying to install ubuntu on my macbook (version 4,1).  It goes normally from bootcamp (and I followed the wikizz people gave me) and it installs from the live cd as it normally does.  The problem is that when I restart at the end, and hold down on the alt-option key, only the mac os partition appears, and I can't boot into linux.  I think the problem is with the partition format, in ext3, which maybe the firmware cant/wasnt designed to use?  im NOT using rEFIt AT ALL because i don't want to screw with the efi boot up.  Is there any way to fix this, or otherwise format the drive in something like fat32?

btw the live cd works perfectly and everything, and the install goes smoothly the only thing is that it can't boot up when i restart, for some reason
thnx!
--BeeLaiyKe

---

### Post by cyberdork33 on 2008-07-16
You need rEFIt, at least temporarily. rEFIt installs on you Mac partition. Nothing in EFI is changed. This is because of a bug in the Hardy installer.

See the FAQ in this forum...
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

