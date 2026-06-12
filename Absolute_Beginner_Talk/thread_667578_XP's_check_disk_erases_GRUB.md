---
title: "XP's check disk erases GRUB"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tstack77 on 2008-01-14
I get this problem when I try to boot into XP after installing gutsy. XP check's the disk (i'm assuming because ubuntu resized it) and then boots into XP. When I restart GRUB is gone and XP boots :confused:

What do I do to get my options back?

---

### Post by SOULRiDER on 2008-01-14
You'll need to reinstall GRUB, check this link out, it explains how to do it.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Just ask if you have any questions.

---

### Post by tstack77 on 2008-01-14
NICE! Looks straight forward enough using the liveCD!

Side question about EasyBCD, will it work with XP too or just Vista?

---

### Post by SOULRiDER on 2008-01-14
I believe it works on both. If it happens to not work in XP you can install grub manually, I can guide you through it.

---

### Post by ronmarley1 on 2008-01-14
Another option to reinstalling GRUB is to use the SuperGrubDisk.  You can download the iso here: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
You boot the CD, walk through the steps, it finds GRUB and reinstalls it.  Reboot and you're good to go.

---

