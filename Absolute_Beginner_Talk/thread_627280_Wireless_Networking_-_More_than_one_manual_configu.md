---
title: "Wireless Networking - More than one manual configuration?"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by somegirl on 2007-11-29
Here's the situation: I have a laptop and successfully got the wireless card set up to connect to my WEP secured encrypted router at home. The way I did this was following the instructions here: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I do a lot of work away from home, at various coffee shops with no WEP encryption. When I first booted at a location with no encryption, it still runs in the manual mode and doesn't give me the option to connect to other routers. I tried this code (from the previously mentioned thread):

> 
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>


It's kicking back a device not found error when I do the 
> 
sudo ifconfig <interface> up

part. 

Any suggestions on configuring my network stuff to be able to get on my secured network when I'm at home and still be able to find and connect to unsecured connections when I'm away from home? I really like ubuntu and would love to be able to use it no matter what kind of wireless connection I'm jumping onto.

---

### Post by Bigbird999 on 2007-11-29
Try wicd.  It replaces network manager and works really well because you can see all available networks and you can select which one you want to connect to,  You can also select a  connect to this network automatically box on your home network, it automatically connects as soon as you get within range of your network.  

IMO it is much better than the gnome network manager..YMMV,  but for me it was painless to install and is rock solid.  

BB

---

### Post by somegirl on 2007-11-30
Is there a way to change the configuration to connect to the open network so I can install this?

Right now I have no working internet connection while running ubuntu so apt-get won't work, unless it's on the install cd and I can pull it off of there.

---

