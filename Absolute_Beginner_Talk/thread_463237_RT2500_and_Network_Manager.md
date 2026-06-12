---
title: "RT2500 and Network Manager"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Manosdoc on 2007-06-03
Please can anyone help me, detailed (I don't know much of instructions) how to make my Ralink Connect to my AP? It seems to open it's leds, try to connect but then it closes
The Network manager semms to "forget" some of my configs.
I now use windows to post:(

---

### Post by rich.bradshaw on 2007-06-04
ndiswrapper will likely help. There are hundreds of tutorials on how to use it on this forum.

---

### Post by bromix on 2007-06-04
what sort of security do you use for your AP?   I can post you a link to a tutorial specific for ya.  I have the same card.  Just some quick copy and paste and you'll be posting here from Ubuntu! :)

---

### Post by Manosdoc on 2007-06-04
Okay! Thanks for the reply! Bromix, the AP is without encryption ( I have some reasons ). Actually I followed a tip looking here in the forum. The RT2500 needs to be downed, then change essid manually, before it can work again.
so I do
sudo ifconfig ra0 down
iwconfig ra0 essid "network"
ifconfig ra0 up
Tada... it works....

I just want you to guide me to install the new drivers Ralink provides, so I won't have to bypass this bug...
I think there is an open-source project RT2XX (something like that) which gives the drivers but I don't know how to Install them to my kernel or something like that.

By the way... Ubuntu found the new Linux kernel 2.6.20-16 and installed it (also with an option to the Grub)
How do I remove the old one ?

Thank you!:D

---

### Post by bromix on 2007-06-05
Manosdoc, from a terminal, type 

gksudo gedit /etc/network/interfaces 

when the file comes up....    add a line "auto ra0"    (without quotes)

try rebooting...it should work   let me know if it doesn't.

heres a copy of what mine looks like-------



# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto ra0

iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "XXXXX"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="XXXXXXXX"
pre-up ifconfig ra0 up

---

### Post by bromix on 2007-06-05
> **Manosdoc said:**
> By the way... Ubuntu found the new Linux kernel 2.6.20-16 and installed it (also with an option to the Grub)
How do I remove the old one ?

Thank you!:D

You can remove the old kernel if you would like.  But....I usually leave two entries in my GRUB.  The current one....and the previous one.  Just in case I run into a serious bug or problem...then I know I have a the older more stable kernel to boot to.   When the next kernel update comes out....or if you want to remove it now...

Go to System-->Administration-->Synaptic Package Manager

Search for linux-image   

Look for the entries for the old kernel and uncheck them...marking them for removal.  This should also take care of any old packages no longer needed, as well.

---

### Post by Pollywoggy on 2007-06-06
> **rich.bradshaw said:**
> ndiswrapper will likely help. There are hundreds of tutorials on how to use it on this forum.

I have a built-in Ralink rt2500 and I used the Ubuntu tutorials and howto's to get it working.  Ndiswrapper is not needed for this card.  I used RaConfig but the card will work with just editing of /etc/network/interfaces and installing of the rt2500 driver.

BTW getting this card to work in kubuntu required some tinkering but in Linspire and Freespire, it just works without much to do in the way of setup.  The next Freespire version will be Ubuntu-based.


Here is the config that works for me in /etc/network/interfaces:

iface ra0 inet dhcp
 pre-up ifconfig ra0 up
 pre-up iwconfig ra0 essid myssidhere
 pre-up iwconfig ra0 channel 7
 pre-up iwpriv ra0 set AuthMode=WPAPSK
 pre-up iwpriv ra0 set EncrypType=TKIP
 pre-up iwpriv ra0 set WPAPSK="mypasswordhere"

I start the connection from  System Settings > Network in kubuntu

---

### Post by Pollywoggy on 2007-06-06
> **Manosdoc said:**
> Okay! Thanks for the reply! Bromix, the AP is without encryption ( I have some reasons ). Actually I followed a tip looking here in the forum. The RT2500 needs to be downed, then change essid manually, before it can work again.
so I do
sudo ifconfig ra0 down
iwconfig ra0 essid "network"
ifconfig ra0 up
Tada... it works....

I just want you to guide me to install the new drivers Ralink provides, so I won't have to bypass this bug...
I think there is an open-source project RT2XX (something like that) which gives the drivers but I don't know how to Install them to my kernel or something like that.

By the way... Ubuntu found the new Linux kernel 2.6.20-16 and installed it (also with an option to the Grub)
How do I remove the old one ?

Thank you!:D

Oh I see you got it to work.

'apt-get remove linux-image-2.6.17' or similar would be used to remove the old kernel but I suggest leaving it where it is because having a backup is a good thing if the other one breaks.

---

### Post by bromix on 2007-06-08
Odd when people post exactly what you did....like my post wasn't even there....LOL

---

### Post by Pollywoggy on 2007-06-08
I should have taken the time to read all the replies before posting.

---

### Post by crispy_420 on 2007-06-08
Feisty uses network-manager by default now. 

rt2500 does not support linux WPA extensions.

Network-manager requires linux WPA extensions.

So basically rt2500 based cards will not work with network-manager, the default wireless manager for Feisty. The only solution would be to remove network-manager and connect the "old" way (think pre-feisty and manually adding essid).

[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

Wish it was different but it is not. Do yourself a favor and get a different chipset. I did just that and I have no issues at all on two laptops (one Intel Pro chipset and the other atheros based).

Also don't hope for too much for the future either. There will be no updates to rt2500 driver from serialmonkey onlt small patches.

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

But it may be temp freeze in development.

---

### Post by Pollywoggy on 2007-06-08
Network Manager and the other gui's never worked for me with the rt2500, now I know why.

---

### Post by crispy_420 on 2007-06-08
Good news is that in the near future there will be a common wireless driver for linux coming out in the near future. So maybe all these wireless issues will be a thing of the past.

---

### Post by sledhead45 on 2007-06-10
a common wireless driver would be most excellent. 

My issue is when using ndiswrapper 1.46 with network manager 0.6.4, is that it will not associate 
with my wireless network unless I first switch the wireless network i'm connecting to. For example, I have 2 wireless networks available, one with wep encryption and one without. In order for me to connect to the unencrypted network i first need to attempt a connection to the encrypted one. Only then can i connect to the unencrypted network without a problem. I've searched the forum and web pretty well without much luck. Any thoughts on this?

--travis

---

