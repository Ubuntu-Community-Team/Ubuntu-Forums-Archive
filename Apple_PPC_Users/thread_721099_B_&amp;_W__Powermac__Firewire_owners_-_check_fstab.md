---
title: "B &amp; W / Powermac / Firewire owners - check fstab!"
date: 2008-03-11
forum: Apple PPC Users
---

### Post by stream303 on 2008-03-11
Wow - this could be big for some owners.

I was skulking around the Gentoo-PPC forums, when I saw it:  a reference to check to make sure that your /etc/fstab is pointing to the right drive after install.

Apparently, some machines have dual hd drivers, like the B&W, and some Powermacs, and when the install is done, it may not be pointing to the right drive.  You may have to boot into rescue-mode from an install disk to check this.

In my case, I'm using Ubuntu and Debian on both my G5's internal drive and external firewire drive and guess what?  The /etc/fstab on my firewire was wrong, pointing to the internal drive.  Even though I manually had to edit my firewire yaboot.conf, I never thought to look at fstab on the firewire drive.  It was only luck that it booted, since both drives have the same partitioning layout - but was probably the source of my random corruption issues.  Ok, fixed!

I'm wondering if in addition to the other usual suspects we have to deal with like sometimes manually editing yaboot.conf, manually editing xorg.conf, that it is also a good idea to check /etc/fstab, especially if you have a dual-drive setup, or a box that uses dual drivers. Thanks, Gentoo!

---

