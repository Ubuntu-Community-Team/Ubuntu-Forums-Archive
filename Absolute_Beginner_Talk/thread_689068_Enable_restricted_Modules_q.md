---
title: "Enable restricted Modules q"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Ex-windows on 2008-02-06
Hi all, 
I just got Gutsy on My new Laptop and trying to figure out The  madwifi or some sort of network manager. So as to set up a wireless connection.
It is an Atheros  ar5006?? Built in card .I installed (via synaptic) the madwifi tools but then thought  I had to download the actual program. However madwifi.org say s it should already be installed with Gutsy. Do I need to enable the restrcited driver  or something?
And would this be the command?
sudo apt-get install linux-restricted-modules

I ran " lshw -C netwrok"  and it shows the device as "unclaimed" 
The tutorial here
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
suggests that the driver is not installed correctly?
ANy Help would be greatly appreciated

---

### Post by spiderbatdad on 2008-02-06
there should be a few...browse them with synaptic package manger. If you installed Gutsy without a working connection, your sources.list may be commented out. If you run into trouble with synaptic, please navigate to /etc/apt/sources.list and ensure your sources are available, or copy and post the list back here.

---

### Post by Ex-windows on 2008-02-06
Thanks 4 Quik response
I have all software sources enabled and the canonical third party one checked as well. I just  downloaded wireless assistant but when I tried to open it I get erros saying: 
Unknown encoding of:8? (funny box):///usr/share/applications/kde/wlassistant.desktop
Since it is kde willl i need to install the kde libs and all that?
But SInce I have the sources are checked where would the madwifi thing be???:confused:
Really:confused:
Quik edit.
I didnt realise what you were saying  but yes I have those restricted Modules checked
Amazing what happens when I look at the pictures lol

---

