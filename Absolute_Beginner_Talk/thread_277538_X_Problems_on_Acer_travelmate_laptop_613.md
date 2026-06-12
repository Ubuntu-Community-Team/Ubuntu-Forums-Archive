---
title: "X Problems on Acer travelmate laptop 613"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by mongee on 2006-10-14
Hi,

I have just recently installed Ubuntu on an Acer Travelmate 613 TVX, but have come a bit unstuck.

I did a network install (using Autralian Ubuntu mirrors) via a PXE boot (CDROM drive is not working), however when I did the first reboot the login screen came up at a command line (not a graphical login as I was expecting).

I have gone through *dpkg-reconfigure xserver-xorg* and checked through there. The setup appears to correctly detect the video card (it picks an i810, Acer laptop has an intel Intel 815EM video card as listed [here]("http://www.ciao.co.uk/Productinformation/Acer_TravelMate_613TXV__5377541#Display")).

I have also tried using the VESA option just to make sure, but basically when I use the command *startx* basically the screen gets a crosshatced looking pattern, the mouse cursor appears (as a large cross) and a small command window appears in the top left of the screen (I type exit and it closes the X session).

The only errors I can see on the console are errors relating to the Wacom devide which in other forums/posts people say to ignore.

Any help greatly appreciated. :)

---

### Post by mongee on 2006-10-14
Am just checking to see if I have accidently done a server install. Will see if info from this [site]("http://www.psychocats.net/ubuntu/nox") will work.

---

### Post by mightyteegar on 2008-02-19
Apologies for digging up an old thread, but I have the very same laptop and wanted to pass along my help.  

AFAICT, either the newest kernels or the latest i810 drivers simply don't play well with the 82815 chipset found in the 613TXV.  I literally tried a dozen different distros as well as Windows XP -- which also didn't work -- before figuring this out.

I finally installed Debian with an older kernel (2.6.18 -- it's the same kernel their LiveCD uses, which is what clued me in) and now it works great.

---

