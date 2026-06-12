---
title: "Wireless Network Setup"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by m60dude5 on 2008-03-24
Hi, I have just installed Ubuntu on my computer but I cannot connect to my home network. Here's the situation:
I have a network that is NON broadcasting SSID, "FULLWIFI". It has WPA encryption. I have been able to connect all of my Windows XP boxes with no problems. In Ubuntu, I clicked the network icon, and clicked "connect to another network" under wireless options. I put in the SSID name, and the WPA phrase, edited the DNS options, etc. and clicked connect. Nothing happens. What can I do to get it up and running. I know all the IP addresses for the router etc, that I would need to enter, I just can't figure out how. Thanks for any help.

---

### Post by Sam Lars on 2008-03-24
What is the output of
```
lspci
```
in a terminal window?

---

### Post by Travisher on 2008-03-24
Hi,
You probably need to check what type of wifi device you have installed in your PC and then search on the ubuntu forums to find specific instructions.

Open a Terminal window ( applications | accessories | Terminal )

then type the following;

sudo lshw | less
password: <your-password>

This will give you a huge list of stuff, use the down arrow key to scroll through looking for wifi device in the list.
If you have a common PCI card or USB stick wifi you may well see something like RT2500 or RT61 as the model - note this for future searches of forums.
Also try;

sudo iwconfig

This will list the interfaces and with any luck include one that is wireless and its current state. 

sudo iwlist eth1 (or whatever yours shows up as) scanning

will give you a list of APs it can see with info on each.
you might try;

sudo iwconfig eth1 (or whatever yours shows up as)  ESSID your-AP-name
sudo iwconfig eth1 (or whatever yours shows up as) key pass-phrase

if it seems to accept this, do iwconfig again to see, then run the following command

sudo dhclient eth1 (or whatever)

If you are dead lucky it will return an ip address and you will be connected but probably you need to arm yourself with the chipset model number and find the various how-to instructions on the forum.

---

### Post by m60dude5 on 2008-03-24
Ok that says a ton of stuff and since im not on the network, i can't copy and paste (on a laptop now) but i;ll include the network card:
```

Network Controller: RaLink RT2561/RT61 802.11g PCI

```

All the other stuff is for video adapters, etc. Thanks for the reply.

---

### Post by m60dude5 on 2008-03-24
ok. I did the iwconfigs, and it recognizes that there is a wireless network. It says that WPA is on which is true. 

What do you mean by "Whatever" in the (). Sorry I am very new to this.

---

### Post by Travisher on 2008-03-24
yep thats the one!
I believe that the default driver fails. Look for instructions on the forums for installing that and RT2500 which is a similar chipset.

---

### Post by m60dude5 on 2008-03-24
Thanks. Where can I find information on the forums about that?

---

### Post by Travisher on 2008-03-24
the whatever means substitute whatever iwconfig shows as being the ethernet connections name.

I've seen eth1, eth2, Wlan0, Wifi1 among others. I'm not sure why but the machine I've got in the garage shows eth2 but the one in my sons pc says wlan0. So substitute whatever it seems to be called.

---

### Post by Helios38 on 2008-03-24
Question..


what card are you using?


do you need ndiswrapper for this card? it is possible that ubuntu does not have the correct Linux driver for your card.


my linksys usb uses ralink chipset, and i had to use ndiswrapper, that may be your problem.


if you need any help with ndiswrapper, PM me.

---

### Post by Travisher on 2008-03-24
You should look at previous postings on RAlink and RT2500 chipset howtos, the drivers are from serialmonkey.com where you may find some instructions better written than my ramblings.
Also I downloaded WiCD to replace the default network manager. That seems to help.

---

### Post by m60dude5 on 2008-03-24
I am using a RaLink wireless card. I haven't figured out how to install ndiswrapper yet (i have it on a cd) but I am trying. Thanks for the replies.

---

