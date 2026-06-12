---
title: "Installing Ubuntu Feisty from CD"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by cmp1988 on 2007-07-29
Hello, 

I'm having trouble installing Ubuntu through the CD.  I'm using the latest version (Feisty).  The install works fine up to the installation of the boot loader.  How would I install the boot loader on the MBR when the disk reads (sda1)?   I've never ran into this problem with previous installs of Ubuntu.  It read (hda1).  The boot loader wants to install into (hd0), but when it does install, the boot loader doesn't show up and I'm forced to boot into Windows.

---

### Post by Frak on 2007-07-29
You ever try burning a [SGD]("http://supergrub.forjamari.linex.org/") and fixing the Grub via that?
You could also try [Grub for Windows]("http://www.geocities.com/lode_leroy/grubinstall/").

---

### Post by cmp1988 on 2007-07-29
That sounds interesting, but I'd like to know if there's a way to work around this problem with the Ubuntu installer.  Thanks for the links in case there's no other way.

---

### Post by cmp1988 on 2007-07-29
Any ideas on how I can fix this?

---

### Post by logos34 on 2007-07-29
What's does your menu.lst show?

Boot the Live cd and mount your root partition.  Post /boot/grub/menu.lst.

---

### Post by vanth13 on 2007-07-31
I'm having the same problem... trying now to install just putting in the expert button () instead of (hd0)... if it's not going to work I'll post my menu.lst file...

---

### Post by vanth13 on 2007-07-31
ok...it's not working menu.lst it's empty... how could I INSTAL grub?

---

### Post by vanth13 on 2007-07-31
up up..
I need help... I'm new to linux and can't even install it... if the installation finishes I would at least repair the grub.. but right now I don't know how to do...

---

