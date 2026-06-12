---
title: "dual booting windows xp and ubuntu 7.10 - reinstalling windows"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by min.emerg on 2008-03-23
Hey,

I am currently dual booting windows xp and ubuntu 7.10, and windows has gone tits up. I need to reinstall xp, although im afraid that it will mangle the boot loader (think its grub). How do i go about re-installing xp while keeping my ubuntu partiion unaltered, and retaining dual boot functionality?

Thanks in advance!

---

### Post by Oldsoldier2003 on 2008-03-23
> **min.emerg said:**
> Hey,

I am currently dual booting windows xp and ubuntu 7.10, and windows has gone tits up. I need to reinstall xp, although im afraid that it will mangle the boot loader (think its grub). How do i go about re-installing xp while keeping my ubuntu partiion unaltered, and retaining dual boot functionality?

Thanks in advance!

download the  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") and use it to restore grub after you install xp.

---

### Post by forestpixie on 2008-03-23
Do you not mean [supergrub]("http://supergrub.forjamari.linex.org/") - didn't know gparted was able to do that?

This [page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") details how to do it with the buntu livecd as well as supergrub and a few others.

---

### Post by Oldsoldier2003 on 2008-03-23
> **forestpixie said:**
> Do you not mean [supergrub]("http://supergrub.forjamari.linex.org/") - didn't know gparted was able to do that?

This [page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") details how to do it with the buntu livecd as well as supergrub and a few others.

yeah actually I did lol editing the post to fix it- its late here and i pasted from the wrong sticky note.

---

### Post by min.emerg on 2008-03-23
Thanks very much for the replies - will give it a bash now.

Got another question - where exactly does the boot loader reside? Is it stored on the master partition?

---

### Post by forestpixie on 2008-03-23
Yea believe so - there's more information on this page than you could shake a stick at - well worth the time

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by seshomaru samma on 2008-03-23
> Got another question - where exactly does the boot loader reside? Is it stored on the master partition?
it resides where you install it, the default in the MBR -master boot record

---

### Post by djbsteart1 on 2008-03-23
> **min.emerg said:**
> Thanks very much for the replies - will give it a bash now.

Got another question - where exactly does the boot loader reside? Is it stored on the master partition?

Unless you told the installer to put it somwhere else its in the MBR. Once xp is installed you can boot on live cd and reinstall grub which should pick up buntu and xp.

---

### Post by min.emerg on 2008-03-23
awesome - thanks for the help!

---

