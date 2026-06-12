---
title: "Mac OS X reads CD, Open Firmware won't"
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by kernalsanders123 on 2009-04-01
Hello all, I searched around the forum for this issue, but I couldn't find anything applicable, so here goes:

I'm trying to install Xubuntu on an Imac G3. I downloaded the PPC port of Intrepid, burned it at 9x, and booted it up holding down the C key. However, it doesn't boot into the CD. Next, I tried going into Open Firmware to try and boot from there. Again, no dice. I then went to Google, and I found the help article at the Ubuntu website on installing on PPC systems. So, I tried "boot cd:,\install\yaboot" under Open Firmware, but it didn't work. I then fired up OS X to make sure that it read the CD, which it does. Under Open Firmware, I tried "dir cd:,\" to verify that Open Firmware can read the CD. It spits out: "bad nodePTR, can't open the dir device."

So, basically, OS X can read the CD just fine, but Open Firmware can't. I've also tried several versions of Debian, with the same results.

Thoughts, anyone?

---

### Post by stream303 on 2009-04-03
I'm wondering if you burnt it as a bootable iso, and not just a regular data copy.

When OSX reads the disk, do you see just one iso file, or do you see multiple folders etc?  This will help determine if you have just got it copied plainly (just one iso file) or if it has been created correctly as an iso with multiple directories in it.

---

### Post by kernalsanders123 on 2009-04-03
Actually, I found that I have to leave the CD in for a few minutes before I try accessing it. Kind of odd, but it works.

Hate to change subjects, but I've encountered another issue which I can't find any existing threads on. I can now get it to boot into low-graphics mode. The top and bottom taskbars appear, but the background doesn't load and no icons appear on the screen. Plus, whenever I try to open an application, the loading circle appears on the cursor, then nothing happens. If I try and load the solitaire game, the box for it appears in the bottom taskbar appears for a split second and then disappears. However, I can load the settings manager.

---

### Post by stream303 on 2009-04-04
Hmm.. let me guess - Ubuntu 8.10 ?  If so, avoid that and try going back to 8.04 LTS or perhaps the Jaunty 9.04 testing.  For a first time install, I'd say try 8.04.1 LTS

And, you'll need to manually edit your /etc/X11/xorg.conf file specific to your G3 iMac.  The installer can't obtain the right values from the hardware, (due to the hardware, not the installer) so you'll have to do it yourself.  Check out the PowerPc FAQ and PowerPC Known issues:

[http://wiki.ubuntu.com/PowerPCKnownIssues](http://wiki.ubuntu.com/PowerPCKnownIssues)

You can obtain the right values here, specifically the horizontal and vertical frequencies.

---

