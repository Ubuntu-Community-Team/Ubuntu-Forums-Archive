---
title: "hardy xorg.conf on intel mac mini problems"
date: 2008-06-14
forum: Apple Hardware Users
---

### Post by blk97tt on 2008-06-14
I am having some problems getting xorg.conf configured correctly on an intel 1.6 Ghz Mac Mini running Ubuntu 8.04.

I have gotten Ubuntu 7.10 configured ok in the past on this computer.  I decided to do a clean install of Ubuntu 8.04.  By default xorg.conf is almost empty and has generic entries like "Default Screen", "Configured Monitor", "Configured Video Device".

I tried using my xorg.conf that worked in Ubuntu 7.10 but it doesn't seem to work correctly.  I try to set the resolution in the file but the settings never apply.  I am also having problems with configuring the power options for the display.

I tried running "sudo dpkg-reconfigure -phigh xserver-xorg" but that just creates another generic xorg.conf file.

I also tried running "Xorg -configure".  This creates a new xorg.conf file with a lot of information but it doesnt seem to work correctly either.  One thing I noticed was that my video driver is being identified as "i810".  In my working Ubuntu 7.10 configuration, it was using "intel".  

If anyone can help me get this working or post a working Ubuntu 8.04 xorg.conf file for a intel mac mini, it would be greatly appreciated.

---

### Post by cyberdork33 on 2008-06-14
xorg does not require a detailed config anymore as it detects things on the fly. Regenerate the standard file, and add the driver line to the device section.

---

