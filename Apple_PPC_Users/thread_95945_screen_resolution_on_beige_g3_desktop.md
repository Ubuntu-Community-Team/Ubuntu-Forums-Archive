---
title: "screen resolution on beige g3 desktop"
date: 2005-11-27
forum: Apple PPC Users
---

### Post by macsimski on 2005-11-27
Hello all,

Finally after trying other solutions on this forum and in the wiki OldWorld macs page i found the solution for my problem. The mac resolution for my desktop G3/266 was 800x600. I could not get to 1024x768. It simply was not on the list. I edited the /etx/X11/xorg.conf file in the ctrl-alt-F1 terminal (as sudo) to see if there was something missing. 

My monitor is a Sony 100SX which can handle 1024x768 up to 75Hz without problems, so that was not it. The xorg.conf file included these setting "1024x768" and I adapted my monitor settings to go from 30-98Khz and 50-160, (way to high for this monitor... but it should work)but without luck.

And then I found it. The resolution was on the default 24 bits depth. I changed that to 16 and there was my ability to change resolution. saved the file, switched back to the KDE session with ctrl-alt-F7 and rtebooted the X11 session with ctrl-alt-backspace. (be carefull! all running applications will be terminated!)

Then i started X11 again with startx and my screen turned to standby. Aha! refreshrate to high. I switched resolution a few times with ctrl-alt-plus sign (on numerics side) untill I had a readable dekstop. It was way to small. I opened the Control Center in the KDE menu>preferences menu and selected Pheripherals>Display. there i settled for 1024x768 by 75Hz and hit the Ok button.

And there was my beloved 1024x768 setting!

So the problem is that the standard desktop G3 has not enough memory in the video card to drive a monitor on 24 bits and 1024x768. maybe with a memory upgrade?

good luck!

---

### Post by daller on 2005-11-28
Please post again in order to sign the thread as answered!

---

### Post by macsimski on 2005-11-28
hello,

please can you point me to the howto for this action? looking around in edit mode gives me no clue.:(

---

### Post by skylark159 on 2006-07-19
Macsimski you are AWSOME!!!

Thank you soo much for your advice on that resolution settings.

I ended up using "sudo dpkg-reconfigure xserver-xorg" to change my xorg.conf file but the changes you made to your file helped me track down my problem.

I should note I also have a Beige G3 MT (G3 233) with both the onboard video (ATI 3D Pro I/II Mac64 GT) and a pci video card (ATI Nexus GA). 

I will still be trying to get the Nexus GA card working with X11 but for now just getting the onboard video working is good.

---

