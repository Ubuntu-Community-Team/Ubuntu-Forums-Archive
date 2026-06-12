---
title: "Specific Virtualization Question (QEMU, XP, rdesktop)"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stevej0 on 2007-05-22
I have been using Ubuntu for just under a year, and I recently upgraded to 7.04.  Doing so, I erased my partition with XP (on purpose), and I installed it in QEmu.  I also followed the steps at [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)
Then, I began to follow the SeamlessVirtualization steps at [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Everything is good, except for two issues:
first.
  I run this line in the terminal:
```
rdesktop -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u *name* -p *password*

```
  note: I did change name and password to the username and password without the asterisks.
the terminal returns these lines:
```
Autoselected keyboard map en-us
ERROR: connect: Connection refused

```

Windows has been set up to accept remote desktop control and the username has been added to the list of users allowed to accept remote control.  All other steps have been followed in the tutorials.

second.
   I am hoping to have some communication between windows programs (seamlessly virtualized or the complete OS in QEmu), however I am unsure about mounting a file as a drive in the virtualized OS... the line that I thought it should be is:
```
qemu -hda /media -m 384 windows.img
```
and this would mount my ubuntu media file as hda in the virtualized windows?

Before you all respond (because I already know you will), I've gotta say thank you to everyone who posts on here because there have been countless times that i've searched for help and found it on these forums.  This whole community rocks, so thanks in advance for your help and the time you take figuring it out, all responses are greatly appreciated.

---

