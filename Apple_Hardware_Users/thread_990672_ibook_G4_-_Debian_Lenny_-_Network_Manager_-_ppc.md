---
title: "ibook G4 - Debian Lenny - Network Manager - ppc"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by boydrice on 2008-11-22
Hello,
This is my first post and I appologize if I am posting in the wrong place.  I did my first linux install today on my ibook.  I installed Debian Lenny with Xfce4, I would have tried Ubuntu but I was having trouble with the iso I burned.  The install went better than I expected, however I would have expected to have selected 'laptop' along with standard and desktop, but that wasn't one of my choices.  So everything works great except there doesn't seem to be a GUI network setting so that I can setup a wireless network.  I tried installing Network Manager from Aptitude but I am unsure how to get that to show on my desktop menu.  Sorry this is most likely a really dumb question, but in messing with live cd's I was familiar with some sort of network manager.  Any help is greatly appreciated.

-Boyd

---

### Post by stream303 on 2008-11-23
Network Manager should be a part of the standard install regardless.

To get your wireless to work, you'll most likely need to get hold of the B43xxxx firmware cutter, although I don't see it listed in the repos - I'm not too heavily into wifi, so I can't really help much.  Maybe someone with more XFCE4 experience can pop in as well.

You may want to try again with Ubuntu PPC as it supports airport / extreme pretty well now out of the box from what I understand.

What trouble were you having with the Ubuntu CD, and which version of Ubuntu were you trying to install?

---

### Post by boydrice on 2008-11-23
I tried Ubuntu Ibex 8.10.  If I can't figure Network Manager in Lenny maybe I'll try installing a previous release of Ubuntu.

---

### Post by Leslie Viljoen on 2008-11-23
Go to the console and run "ps -ef |grep nm" - look for "nm-applet". If it's not running, you can run it in the console and it should pop up on your panel. If that works, you can add it to your startup applications using Settings -> Settings Manager -> Autostarted apps. When you add it, use the "--sm-disable" option. 

The bigger problem though is that Intrepid is the only distro I know of that just auto-detects bcm43xx and does all the firmware stuff for you. If that is not done, everything will seem to work but the card will just not connect. 

I am busy trying to figure out the firmware stuff now, so I'll post the steps when I get there - or you can search. If I were you I'd hold off on going to Intrepid for that though, because Intrepid has other problems. Thunar, the main file manager, doesn't even run out-of-the-box.

---

### Post by khelben1979 on 2008-11-23
If you would be interested to go back for Debian Lenny, [then this document]("http://wiki.debian.org/NetworkConfiguration") might help you out in this matter.

Check it out if you're interested.

---

### Post by Leslie Viljoen on 2008-11-23
This seems to be the place for info on the Broadcom firmware stuff:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I'm trying it now.

---

### Post by Leslie Viljoen on 2008-11-23
Nope, mine's not working. I can get nm-applet to load by making it load at startup and putting a "system tray" on my panel. But the b43 driver doesn't seem to be working, as before with Gutsy, even when I follow the instructions to get the firmware out of the broadcom driver. You may have better luck. 

You'll probably follow the instructions for the "b43" driver, check "lsmod|grep b43" to be sure.

Then follow the instructions entitled "You are using the b43 driver from linux-2.6.24", here: [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Godspeed!

---

### Post by boydrice on 2008-11-23
Tried it and it didn't work, going to try Ubuntu Hardy.
Thanks for your help!

---

