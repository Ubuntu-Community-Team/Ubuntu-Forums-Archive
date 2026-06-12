---
title: "partial incurable freezes with Firefox"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by donestephens on 2007-03-25
Hi Folks:

When I visit slashdot.org, cnn.com, hotmail.com, gmail.com, or many other sites (but fortunately, not this one), the Ubuntu Desktop freezes--sort of.  The mouse cursor switches to the icon with the little hand with the extended index finger, and as soon as that happens, the mouse cannot click or select anything, even though I can move it freely.  All keyboard input dies at the same time.  The "networking" icon in the tasktray at the top right of the screen switches to what looks like a frame in an animated icon, but not the one you normally see.  However, even though all these symptoms occur as soon as I hit the enter key after typing in a URL, the browser continues to download the page and properly renders everything, even if that takes several seconds after input has died..  

From other linux I experience, I thought to try Ctrl Alt Bkspc to break out of  Xwindows, but that fails just like any other keyboard input.  I can't get a shell with Ctrl F2 or Ctrl Shift F2 or Ctrl Alt F2 or Shift Alt F2.  Basically input has stopped except that the mouse cursor will move.

I have examined my X.org.0 log and I don't seen anything there that looks like an error.  

I found a post on this forum where someone suggested an edit with gedit of /usr/bin/firefox that had to do with a problem with flash. I tried that fix, but my problem returned when I restarted Firefox, and just for funsies, I tried it again after a reboot, but the problem remained.  

I have looked at the /var/log/messages file, and I don't see anything that looks relevant.  

I am running Dapper Drake, the 6.06 LTS.  This is an Athlon XP 800 Mhz cpu with 256 MB of ram.  My video card is an Nvidia Geforce2 MX/MX 400. 

Generally everything else about this install works without a hitch.  I have a Netgear MA101 USB wireless that pretty much worked out of the box and a usb Samsung Laser printer  that worked with little setup.  

Thanks for reading this. Any input is appreciated.

Don

---

