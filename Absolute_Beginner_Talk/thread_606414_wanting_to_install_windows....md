---
title: "wanting to install windows..."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by wiachy on 2007-11-07
i just put Ubuntu 7.10 on a laptop and i have been using Ubuntu on my desktop, now that i have ubuntu on the go i need to put xp back on the desktop.  how do i do that?  i put the windows disc in and nothing happens. :(

---

### Post by Dr Small on 2007-11-07
Make sure your bios is setup correctly.
By the way, what is your desire to load Windows back in for ?

If it is some application, I am sure we can find an alternative.

Dr Small

---

### Post by vladan.b on 2007-11-07
Stick the xp cd in, reboot.  If nothing happens, then you need to change your bios options so its first boot is off the cd.

---

### Post by MrFSL on 2007-11-07
Sounds like an excellent opportunity to setup a dual-boot system. Have the best of both worlds.

---

### Post by Paqman on 2007-11-07
Also, if you install Windows after Ubuntu you'll have to set Grub up manually, otherwise you won't be able to boot Ubuntu.

---

### Post by wiachy on 2007-11-07
> **Dr Small said:**
> Make sure your bios is setup correctly.
By the way, what is your desire to load Windows back in for ?

If it is some application, I am sure we can find an alternative.

Dr Small

right now im still learning the whole linux thing, now that i have it running on my laptop it is much easier for me then having it on my desktop, plus i need my gaming fix.

---

### Post by ARhere on 2007-11-08
You are going to run into trouble creating a dual boot with Linux on the system first, then installing Windows.  It is easiest if you have Windows loaded first, and then load Ubuntu as  Linux will "play nice" and set up the dual boot for you.  When you load Windows it will assume it is the only OS on the system and you will have to manually reload GRUP or modify the windows boot loader to give an option to dual boot.

I have found [this link]("http://www.linuxforums.org/forum/debian-linux-help/55188-how-can-i-boot-debian-linux-after-have-installed-windows-how-restore-grub.html") to help you.  If not, google "restoring GRUP after loading windows" should help you out.

-AR

---

### Post by wiachy on 2007-11-08
thank you all for the replies!

---

### Post by SomeGuyDude on 2007-11-08
> **wiachy said:**
> right now im still learning the whole linux thing, now that i have it running on my laptop it is much easier for me then having it on my desktop, plus i need my gaming fix.

There are ways to get your gaming fix through Ubuntu. It'll take some added effort, but on the plus side you won't be eating up at LEAST 7 gigs of your hard drive just to have a way to play games.

---

