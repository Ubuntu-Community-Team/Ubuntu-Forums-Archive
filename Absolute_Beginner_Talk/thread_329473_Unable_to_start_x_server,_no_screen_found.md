---
title: "Unable to start x server, no screen found"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by four-four on 2007-01-01
Hi to all!

this is my first post here!

I am a first time user of Ubuntu and know just a little about unix/linux but i am at ease with computers in general (DOS, Win 3.1 to 2000, Mac OSx, just a little netware and unix)

I have a system with a built in video card (SIS 5597/5598 ) with 2Mb ram and a 3DFX Voodoo Banshee w/ 16Mb ram added on.  The bios is set to have the 3dfx card as the primary and i installed Ubuntu using the screen on this card.  Everything seemed to have went well 

On reboot, everything loads and i get a fatal error, no deveice found.

I searched and found this:
[http://wiki.x.org/wiki/FAQErrorMessages#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed](http://wiki.x.org/wiki/FAQErrorMessages#head-c6257ccfbd37c0fa287883d80fb4f1c2724244ed)

and this
[http://www.ubuntuforums.org/showthread.php?t=328763&highlight=no+screen+detected](http://www.ubuntuforums.org/showthread.php?t=328763&highlight=no+screen+detected)

I did find and edit the xorg.conf file as mentionned in the link above.  I found out that it only contains the info on the SIS video card and nothing on the 3dfx.  i commented out the device line and nothing.  went back in the bios, put the onboard SIS as primary and removed the 3dfx and it still did not work, always the same error.

I'm confused, i don't know what other options i have.

Moreover, my original idea was to install ubuntu and leave the computer in the closet, headless and run it with a VNC client or ssh from my mac in my room.

Thanks for the help!

---

### Post by hoges on 2007-01-01
OK, it sounds like you're having a similar problem to what i had. 

[http://www.linuxquestions.org/questions/showthread.php?t=378077](http://www.linuxquestions.org/questions/showthread.php?t=378077)

This is command to change the display drivers: dpkg-reconfigure xserver-xorg (as found on above site).

If it comes up with an error saying "xserver is not installed", or something similar, you'll have to reinstall xserver. I can't remember the command at the moment, but i can find it if you need it.

If the normal drivers don't work, than try the vesa ones. That way you can actually log on, than install the official proppriatry linux drivers that can't be shipped with the install disk.

---

### Post by hoges on 2007-01-01
[http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)

That's the link i used to help reinstall xserver if needed.

---

### Post by four-four on 2007-01-04
Thanks!

I tried to reconfigure with ant without the added video card.  I used the VESA with the SIS built in card and it worked, but the image was rounded out, like out of sink or bad resolution  (and the monitor prompting me to switch resolution)

I finally figured out that ubuntu would see the PCI adress 0:9:0 (the SIS card) and never go to the next one.

So i reinstalled the other video card and tried to reconfigure with the dpkg... and it wouldn't accept the 0:11:0 adress of my other video card.

So i dpkg-reconfigure and then i  nano'd the /etc/X11/xorg.conf to read 0:11:0  


HURRargh...  Xserver starts, i get Ubuntr color background, get some screen flickering while i hear the clikering of resolution switching and i got the chronograph...  but nothing else, no log on nothing...

Almost there...

---

