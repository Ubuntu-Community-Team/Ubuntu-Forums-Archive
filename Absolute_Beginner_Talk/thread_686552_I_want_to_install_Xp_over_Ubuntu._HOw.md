---
title: "I want to install Xp over Ubuntu. HOw?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-02-03
My computer has Ubuntu.
I want to install Xp also to play games,but i couldn't do it.
How can i make?(with dual boot)

---

### Post by jan quark on 2008-02-03
when you install xp over ubuntu 
xp will delete the grub loader and you do have to restore it manually using the [super grub disc]("http://supergrub.forjamari.linex.org/")

have a look at
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by justin whitaker on 2008-02-03
> **rhc said:**
> My computer has Ubuntu.
I want to install Xp also to play games,but i couldn't do it.
How can i make?(with dual boot)

I find it easier to install XP first, then install Ubuntu on it's own partition. I do alot of installs (can't make up my mind) and that still is the easiest way to do it. Ubuntu will overwrite the XP MBR with GRUB, autodetect the XP install, and put it in Grub for you. Way easier than futzing around with GRUB after the fact.

---

