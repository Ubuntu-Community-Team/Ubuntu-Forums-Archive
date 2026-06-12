---
title: "Reinstalling Grub"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-07-03
[COLOR=DarkOrange][B]So i just installed Fedora seven and its kinda messed up my grub, lukily i set it for xp to boot up as default or i'd be in trouble(trip tomarrow and i need to get things done)

What would be the simplest way to get grub back up and running?
[/B][/COLOR]

---

### Post by alienexplorers on 2007-07-03
Try inserting your live-cd and boot up.  Enter terminal and type sudo grub.
Enter:
> find /boot/grub/stage1
You wiull get an output like (hd#,#)
Enter:
> root (hd#,#)
setup (hd#)
quit grub
reboot

---

### Post by dvlchd3 on 2007-07-11
I did this however now when grub and I select which partition to boot it says:

> Error 17: Cannot mount selected partition

Press any key to continue...

Now I can't even boot into windows...what do I do?

---

### Post by ramjet_1953 on 2007-07-11
I have found that the best way to deal with GRUB issues is to download Super GRUB Disk.

It is an iso image that you burn to a CD and boot from that.

It is really great at recovering and re-building hosed GRUB files.

You can download the iso from here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Regards,
Roger :cool:

---

