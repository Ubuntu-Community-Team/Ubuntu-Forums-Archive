---
title: "Ubuntu Server and Wireless"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by bgschley on 2006-07-25
Hi Everyone,

First off, what a great community this is. Thanks! Next... I'm new to linux... but do have some technical IT experience. I am trying to setup a simple print and file server for our home network. I have installed the base server installation but now need to set up the network. For the network, I am using a USB wifi adapter (Netgear WG111). Unfortunately, this is not being picked up - I checked using ifconfig. I have tried to get madwifi using apt-get, but from what I can see, it isn't in the repository (from what I can see).

So, what I need is... some advice on how to set up my wifi adapter on an Ubuntu server machine.

Thanks again.

George ](*,) :eek:

---

### Post by henderb on 2006-07-25
Madwifi is listed in the linux-restricted-modules-*kernel* package.

You may have to add the non-free repositories to get access.

---

### Post by az on 2006-07-25
Run 

tail -f /var/log/messages

and plug in your device.  Post the output.  That may reveal what chipset it is.  Many brands of wireless devices have different chipsets with different revisions.

The madwifi driver is included in the install.  If it was a madwifi device, it should work out-of-the-box.

---

### Post by bgschley on 2006-07-25
Hi there,

I've run tail and the output states:
No suitable configuaration found.

So, from this can I presume that my adapter is not supported by madwifi? If so, can anyone recommend the next steps...

Thanks again for your help... at least it feels as though I'm getting somewhere.

Cheers

George

---

### Post by az on 2006-07-26
You did not configure your device?  You need to edit /etc/netowrk/interfaces to do that.

If you run the desktop cd, and use the networking GUI, you can config your device graphically.  You can then copy the interfaces file and then cut and paste the config to your server (with no gui)

---

### Post by bgschley on 2006-08-03
Hi there,

I setup my config file using info from the following link:
[http://www.ubuntuforums.org/showthread.php?t=101274](http://www.ubuntuforums.org/showthread.php?t=101274)

I then used ndiswrapper to install the xp driver for the wg111.

All seems to be working fine now.

Cheers and thanks for your help.

George

---

