---
title: "Wifi with dapper and network manager?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by megadeus on 2007-05-15
Hey, all, longtime lurker, first time poster. I've been using 6.06 LTS on and off for a few months now (this is my first time using Linux) and one of the main things keeping me on my XP partition is the fact that I can't connect to any wireless networks with Ubuntu.

I'm using a fairly standard-build Dell Inspiron 8600 and I just downloaded 114 updates for Ubuntu (it's been awhile).

I've tried using Network Manager (after seeing so many suggestions to that effect on these forums), but it only shows Wired Connection (which I'm using).

My wireless network currently uses the WPA encryption, but seeing as the Networking tools only seems to support WEP, I'd be willing to switch over (but I'd rather not).

I'm not sure what the connections are supposed to be named, but the wired connection is named [COLOR="RoyalBlue"]eth0[/COLOR] and the wireless connection is named [COLOR="RoyalBlue"]eth1[/COLOR]. I'm very new to Linux, but I seem to recall seeing other names for wireless connections.

Any help would be appreciated. Just let me know what config files to post/edit.

Thanks in advance. :-)

---

### Post by annda on 2007-05-15
dapper needs extras to support WPA, take a look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

i'd recommend upgrading to feisty, it supports WPA out of the box.

---

### Post by megadeus on 2007-05-15
Thanks for the link. I'll give those a try and report back.

I don't think I'll be upgrading to Feisty on this installation, just because I don't want to mess up my dual-boot. Besides, I've read a few posts describing issues with Feisty and wireless.

---

### Post by megadeus on 2007-05-19
Okay, I've tried everything on the above linked page and I still can't get it to work. I have wpasupplicant installed and up-to-date, I installed network-manager-gnome, and neither seems to have helped.

Network Manager only shows the wired connection I'm using to make this post, and when I unplug that connection, no wireless connection is available.

So I'm still here at square one.

Anyone with any other suggestions?

---

### Post by megadeus on 2007-05-21
Bump.

Any suggestions? I really want to be able to work online with linux without having to tether myself to the modem.

---

### Post by icantdothatdave on 2007-05-21
I'm having a similar problem. I am using Feisty, and I used to be able to see all of the wireless connections using the network manager, but now I only see the wired connection. 

I have a few other wonky things going on as well. Up until today I've always been able to use the VPN at work, using the vpnc program, but today it stopped working. It acts as if it's connected, but after connecting I can no longer access web pages, and pinging just gives me "unknown host". The network settings UI also shows weird things going on. It shows tun0 and ppp0 as modem connections, and it displays my wireless connections as wired connections.

I don't remember doing anything in particular to mess with any network settings, except that on Friday I played around with the roaming settings in Network Settings, but immediately changed them all back, after which my connections were still working. These problems didn't come up until this morning. I've tried all the usual rebooting and messing with ifconfig, but to no avail. :|

---

### Post by megadeus on 2007-06-19
Okay! I finally figured out what to do.

Remove network-manager-gnome and the associated applet.

Then install **wicd** from [http://wicd.sourceforge.net]("http://wicd.sourceforge.net").

That's it. This solved ALL of my wireless networking problems in one step. It was easier than falling off a log.

---

