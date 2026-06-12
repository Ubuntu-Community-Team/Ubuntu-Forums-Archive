---
title: "Install Oneiric on an EeePC 701"
date: 2011-11-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by JRV on 2011-11-05
The Oneiric (11.10) desktop live and the alternate install CDs will not work on the Asus EeePC 701 because the four gig solid state drive is to small.  But it is possible using the netboot CD.

The only modification to my 701 is 1 gig ram instead of the standard 512 meg. 

Download the netboot CD (i386) here:

[http://cdimage.ubuntu.com/netboot/oneiric/](http://cdimage.ubuntu.com/netboot/oneiric/)

Burn the .iso, boot it, and do a command line install.

It will probably work to transfer the .iso to a bootable USB stick with unetbootin and boot from that, but I have not tried it.

When you get to the part about automatic updates check to update manually, this has no effect on the graphic update manager.

When the installation is finished re-boot, log in and install the following packages.

```

sudo apt-get install lightdm xorg xinit ubuntu-desktop

```

When it is finished re-boot and you will have a working gui.

Open a terminal and clean up the system with the commands:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

Next you may want to check out my tutorial on Localepurge, it can save a lot of space on a small drive:

[http://ubuntuforums.org/showthread.php?t=1867813](http://ubuntuforums.org/showthread.php?t=1867813)

And now for the review, how well does it work?

Boot time seems very slow, and I get a message that says "Waiting for network configuration...".  
Then "Waiting up to 60 more seconds for network configuration...".
And finally "Booting system without full network configuration".
If I boot with an ethernet cable plugged in it boots much faster and without all the messages.
Once the you have logged in and Unity desktop is loaded it seems acceptable.  
It's no giant killer but then a netbook never was ment to be.
Wireless and wired ethernet work with no problems.  
All the function keys worked as expected.

---

### Post by kgarbutt on 2011-11-09
Thanks JRV for your eeepc trick. I have a 701 too & I think I'll try your trick with xubuntu.

Thanks, Ken

---

### Post by BigSilly on 2011-11-11
This is a pretty neat idea, but to be honest Lubuntu is a much better fit for the Eee 701. We have it on ours and it flies.

---

### Post by Jack Brown on 2011-11-12
LuXubuntu time

 =D> good thing we have these two so it's easier to stay with ubuntu

---

