---
title: "Wireless USB Adapter (E-Tech, Ralink chipset)"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Nizzle on 2007-03-29
Hello :)

I've got a lil problem.. well actually.. my sister has a lil problem..
her windows broke (once again) and she decided she wanted ubuntu cos she really likes it on my pc.. all good and stuff so I gave her the CD (she's a bit n00bish) and she managed to install it all properly.. asking only about our time zone and partitions.. 

anyways on to the problem
she only has wireless lan cos router is crap and only allowes 2 wired connections (who's are mine and my dad's.. she was the only one who had proper connection with wireless)
so now she's got a bit of a problem to get online.. and since I'm fairly new to Ubuntu myself there just isn't much that I could do to help..

did ask around on the Dutch Ubuntu forums but that didn't really help
also google'd a bit but that didn't help either..

so now I come here with my question..
according to the Dutch Forums I had to type this in terminal "sudo lsusb" and post the output

```
Bus 003 Device 002: ID 148f:2570 Ralink Technology, Corp. 802.11g Wifi
```

that was the interesting part of that..
then they said to take a look at this howto.. [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)
but that didn't help one bit since she uses Ubuntu Edgy 6.10 and it should be working out of the box..
after that I was told to disable all protections on router.. did that and still nothing..

later on she said the whole wireless wasn't even enabled (in network tools) so we enabled it and tried again.. still nothing
now I don't have a clue what to try next..

though there is one thing.. in the network tools thingy they ask for ESSID.. when I looked in our router settings what the hell that might be I only found SSID.. assuming that that would be the same I just filled in that..

please help us out :(
she keeps asking me like every 5 mins.. :lolflag:

---

### Post by crispy_420 on 2007-03-30
First of what security settings are you using? (wep or wpa)

SSID = network name

Then you will need to use a passphase/key to get into network. This will be very similar to setting up in windows. You may as well disable your wired network so that ubuntu only has one option for a network connection.

You may need a wired connection temporarily to setup.

---

### Post by trent dillman on 2007-03-30
...

---

### Post by Nizzle on 2007-03-30
disabled all security settings.. (there's no need for them anyways, who'd want to hack MSN messages..?)

and the wired network is disabled in network tools..
also I'd be hard to download and install the drivers without any internet right :-/

weird thing is with the settings they ask for ESSID.. I filled in the SSID cos that seemed the same thing to me.. then they ask for password.. but there is none :(

---

### Post by rich.bradshaw on 2007-03-30
ESSID is the SSID if you are still unsure.

can't you just leave the password blank?

When you have got it working you should def renable security and set it up properly, it's not about hacking, it's about someone pulling up outside your house, downloading child porn and then you getting the blame as it was downloaded via your connection.

---

### Post by crispy_420 on 2007-03-30
You may want to turn on security again once you get set up. Or even when you are not setting up the network. Your concern should not be people hacking your MSN account but what people could do with your connection.

I know people that drive around looking for an open connection. Sure they just check their email but they could do worse. Say for example they could use your connection to view websites that have illegal material or even commit a crime. And you know what, it came from you as far as the authorities are concerned. I know it is an extreme but it could happen.

---

### Post by Nizzle on 2007-03-30
> **trent dillman said:**
> Try using the drivers from the manufacturer.

```

sudo -s -H
apt-get -y install build-essential
cd /usr/src
wget http://www.ralinktech.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz
tar zxf RT73_Linux_STA_Drv1.0.3.6.tar.gz
cd RT73_Linux_STA_Drv1.0.3.6
./configure
make
make install
exit

```

WARNING: I'm not 100% on the exact commands here...

tried this.. doesn't work :(
in fact it can't configure or make install :( :confused:

---

