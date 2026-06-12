---
title: "Display problem for login window"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Nakamura2828 on 2006-12-20
Hi, I'm new here, and in the process of setting up my first Linux box. I'm at best a novice with *nix, having only used command-line Unix & Knoppix from a live CD in the past. Anyway, I just installed Ubuntu Edgy Eft 6.10, and by and large the installation went off without a hitch. My only issue was that the default display drivers wouldn't allow me to run at above 800x600. I went ahead and downloaded & installed ATI's proprietary Linux drivers for my Radeon 9800 Pro and ran into a weird problem.  When logging into Ubuntu, I get a problem with the refresh rate being out of bounds for my monitor (actually I tried a few monitors and can't get one that works).  If I go ahead and log-in blind, everything is fine and the display runs in 24-bit mode 1280x1024 @ 60 hz (which is where I'm typing this from right now).  After browsing a bit, I found a few potential fixes (booting with VGA=791 from GRUB, editing /etc/X11/xorg.conf in a number of ways, running through dexconf), but none of it seems to fix anything. I also tried changing the login window properties from within Ubuntu and it seems to have no effect whatsoever. I'm mostly confused by the fact that on the whole the drivers are working perfectly, but not for the login screen. Anyway I'd appreciate any help you guys could send my way.  Thanks a lot.,

---

### Post by maxamillion on 2006-12-20
open a command line Terminal and type > gedit /etc/X11/xorg.conf

then copy and paste that to [http://ubuntu.pastebin.ca/](http://ubuntu.pastebin.ca/) and then post the resulting link and we can work from there

---

### Post by Nakamura2828 on 2006-12-20
> **maxamillion said:**
> open a command line Terminal and type 

then copy and paste that to [http://ubuntu.pastebin.ca/](http://ubuntu.pastebin.ca/) and then post the resulting link and we can work from there

Here's the URL: [http://ubuntu.pastebin.ca/286806](http://ubuntu.pastebin.ca/286806)

As far as I know all the color modes & resolutions should be fine for my setup. I also tried things such as changing driver from "ati" to "radeon" which I'm guessing isn't what I want to be doing if I want to use the drivers I installed. (It didn't work anyway)

---

### Post by Nakamura2828 on 2006-12-21
Just thought I'd bump this to see if anyone could make heads or tails of my situation & have any ideas on what to do to resolve it. Thanks.

---

