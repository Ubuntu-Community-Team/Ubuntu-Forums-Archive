---
title: "Installation Woe"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by blaa on 2006-11-08
Hello :)

I'm on a bit of mission to set my machine up with Dual Boot Ubuntu and XP. I have a small amount of linux experiance (I have installed it successfully before, but never really used it), but not on the machine I have right now.

I have set up the partitions as per [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) (very useful site found here) and it all seems to install correctly enough.

I go through GRUB click the right ubuntu, it goes to load, and I get to the last 90% and blue lines appear across the screen, then a solid green line, then the system just sits there.

I get the same result with the Live CD.

My specs are:

Pentium 4 3.0 Ghz
Gigabyte 915MF Intel i915 Chipset
Radeon X800GT
M-Audio Delta 1010

Can anyone help? - or lead me in the right direction?

---

### Post by Sef on 2006-11-08
If you run the Live CD (as a Live CD), are there any problems?

Could be that your disk is bad, or your download or burn was bad too.

---

### Post by blaa on 2006-11-08
Yep tried the Live CD (6.10), as a seperate download, then downloaded the alternative CD as the Live didn't work.

---

### Post by blaa on 2006-11-08
Ok, so I downloaded Dapper alternative CD, deleted the edgy eft partition, put dapper on instead. Installing was fine..

..it tells me however that it failed to start X server.

'Using config file: "/etc/X11/xorg.conf"
 (EE) No devices detected.'

I tried doing a sudo dpkg-reconfigure xserver-xorg but I am completely lost.

Am I correct in assuming that my graphics card is at fault here?

---

### Post by blaa on 2006-11-09
righto!

So I found more info on xserver, 

[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
[http://wiki.serios.net/wiki/Determining_the_video_card%27s_bus_identifier](http://wiki.serios.net/wiki/Determining_the_video_card%27s_bus_identifier)

and now can load into my desktop because I have switched to vesa drivers.

But how come I can't see any tool bars? just have two hard disks on the desktops and thats it..

---

