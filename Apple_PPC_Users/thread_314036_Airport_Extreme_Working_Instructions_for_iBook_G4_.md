---
title: "Airport Extreme Working Instructions for iBook G4 - Edgy Install"
date: 2006-12-06
forum: Apple PPC Users
---

### Post by webman2k on 2006-12-06
Hello all,

I tested this twice to make sure it would work the first time each time.  I've successfully gotten AE to work on an Edgy installation.  I have an iBook G4 (late 2004 model).  Your results might vary:

1. Connect the computer via ethernet cable, and install Edgy along with any available updates.

2. Enable the "Universe" repository from System > Administration > Synaptic Package Manager.

3. Download the following file, and copy it to your desktop:
[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)
If that link is dead, just google the file name and find a working download.

4. In terminal:
sudo apt-get install bcm43xx-fwcutter
cd Desktop
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
sudo modprobe bcm43xx

5. Now set up your wireless in System > Administration > Networking

6. Close Networking, and unplug your ethernet connection ;)

Wireless works upon restart perfectly, annd hasn't dropped out in over a day.  It seems to be at 11M transfer, but I'm not going to complain - it's working! If you have trouble, try deactivating the wired connection in Networking - I had to do that on the second try. You can turn it back on later if you need it.

Based on instructions found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

-Mark

---

### Post by samden on 2006-12-08
I must say, this sounds very promising. I do not currently have an airport card in my iBook G4, and at present OSX is fine for my needs on that machine. But I expect I will eventually want it running linux as it gets older, and may consider getting an airport card for it. This raises my hopes a lot about the future usability of this machine.

---

### Post by ipina on 2006-12-09
"sorry, the input file is either wrong or not supported by bcm43xx-fwcutter, I can't find the MD5 sum ffaaa ... 70e" is the message that I got, any suggestion? thanks in advance

---

### Post by handylinux on 2006-12-09
Worked for me (iBook G4 1GHz); thanks for making the procedure simple enough for a Mac user to follow.

Oops... After I wrote the above, the phone rang, and as I spent some time on the call, the iBook (running on battery) went dark. I thought maybe it had gone to sleep -- though the sleep light wasn't pulsing -- but when I touched a key, it lit up again. But the AirPort connection was lost.

So I tried the final suggestion: turned off the wired connection and restarted. And AirPort was back, and has worked consistently on several subsequent restarts.

Sorry, ipina, this is my first Linux command-line adventure (after 18 years with the Mac), so I can't address your question. I did note that the following text appeared during the process:

> Sorry, it's not possible to extract "bcm43xx_microcode13.fw".
Extracting firmware from an old driver is bad. Choose a more recent one.
Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
But this can be added in the future...

which I was guessing might have something to do with webman2k's original note that he's getting only "11M transfer", which I'm guessing means "b" (original AirPort) rather than "g" (AirPort Extreme) speed.

Anyway, it's working now, and I'm using iBook + AirPort to enter this post.

---

### Post by handylinux on 2006-12-09
And the AirPort connection quit again, about a minute after I entered the post above. This time I opened System: Administration: Networking, and unchecked Wireless connection, then checked it again. Which apparently forced it to try to make the connection again, which it did, and now it's working again.

So why does it just quit, without warning, and apparently for no reason?

---

### Post by ipina on 2006-12-10
Thanks anyway for your reply. I'm not an expert but seems to me that there are some problems with the firmware. Ok I'll keep examining the issue so in case I get some consistent solution I'll communicate it. Cheers.

---

### Post by dshan on 2006-12-13
I assume none of you who go this working with the bcm43xx firmware are using encryption? WPA specifically. Installing the bcm43xx firmware certainly got rid of the missing firmware messages I was getting in syslog when trying to connect to my AEBS from my Al PB G4 (Edgy), but it still won't connect and I think the problem is that I'm using WPA encryption. 

I've beaten my brains out over the last few days trying both wpa_supplicant (with both wext and now bcm43xx drivers) - no luck, and Network Manager, also with no luck (supposedly NW Mgr will work with WPA on PPC Macs if you paste in the hex passphrase returned by wpa_passphrase instead of the plaintext version in the password field, but it doesn't work for me).

If anyone has managed to connect to an Airport Extreme BS using WPA and bcm43xx from either an Al PowerBook or an iBook G4 I'd love to hear how you did it...

---

### Post by Efros on 2006-12-14
> **handylinux said:**
> And the AirPort connection quit again, about a minute after I entered the post above. This time I opened System: Administration: Networking, and unchecked Wireless connection, then checked it again. Which apparently forced it to try to make the connection again, which it did, and now it's working again.

So why does it just quit, without warning, and apparently for no reason?

You don't have a cordless trelephone do you? If you do try setting your router to broadcast on channel 11 only. 2.4GHz cordless telephones mess up wireless networks unless the network is restricted to channel 11.

---

### Post by handylinux on 2006-12-14
> **Efros said:**
> You don't have a cordless trelephone do you? If you do try setting your router to broadcast on channel 11 only. 2.4GHz cordless telephones mess up wireless networks unless the network is restricted to channel 11.

Thanks for the suggestion. I do have a cordless phone, but I checked my router (a NetGear DG834G DSL Modem / Wireless Router) and it is set to Channel 11. And my Mac's connection doesn't drop mysteriously. Seems clear the problem is/was in the software in the Linux setup; since I turned off the wired network as suggested, the AirPort connection has been fine through several sessions.

PS: Seems I spoke too soon. Just to spite me, I suppose, the AirPort connection just quit again, in the middle of a session. I went to Network Settings, turned if off and on again, and now it seems to be working again. For how long?

I'm planning to switch my Ubuntu to a PowerBook G3 once it's up and working; I understand its original AirPort card works with Ubuntu out of the box (as did one in an iBook G3). But it is an annoyance that AirPort Extreme is such a hassle. I wonder how it is with the Intel Macs?

---

### Post by Synthetic420 on 2007-01-16
[SIZE="3"][COLOR="DarkRed"]Hey, great post.  Very semi-User Friendly.  A hell of a lot better than other tutorials just assuming that you know everything about Linux, which is asinine, because most people installing the card are probably dealing with a fresh copy of Linux for the first time!!  

OH!!

ATTENTION:  ::STILL HAVING PROBLEMS??::

Here are some pointers that I had to go through:

1.  If you're having trouble connecting, and have a cordless phone, log into your router(type in it's domain address into the address bar, which should be 192.168.0.1, 192.168.1.1, or if you have a Microsoft router, 192.168.2.1) and access the Wireless settings.  From there, change the output channel(channel 6 on default) to 11 and click Saves Changes (some routers auto-save.  If yours is a Linksys, you have to save first.)  ALSO, if your router supports channels 12-14(I think they're illegal in USA), having a higher channel is always better quality and speed, given that all of your wireless devices use the bcm43xx, because thats the only wireless chip that I know of that has ch 12-14 support.  If your not sure which of your devices support the extra channels,  every TrendNet USB card, and almost every LinkSys USB card has  the bcm43xx chip in them.

2.  If you're getting a slow rate, and you're close to your router(e.g. 11Mps or lower), or you still can't connect at all, go into the router's wireless settings(see # 1.), and change the Wireless Mode(if it doesn't say Wireless Mode, then look for an option to change between G, B, or Mixed) and change your connection from G to Mixed.  This will allow more support, and ultimately give you faster speed.  After you've changed it to Mixed Mode(G and B), go into the terminal(Applications, Accessories), and type in the following:
```
sudo iwconfig eth1 rate 54M
dmesg
```
Where "eth1" is might be different for yours.
The dmesg is to see if it says:
```
[ 1445.099463] ieee80211_crypt: unregistered algorithm 'NULL'
[ 1450.657294] ieee80211_crypt: registered algorithm 'NULL'
[ 1450.674821] ieee80211: 802.11 data/management/control stack, git-1.1.13
[ 1450.674842] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 1450.731003] bcm43xx driver
[ 1451.624694] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1451.963284] SoftMAC: Open Authentication completed with 00:0d:3a:25:6b:d1
[ 1451.975313] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

```
If it stops at "Open Authentication completed with ......", then try this:
```
sudo modprobe -r bcm43xx
modprobe bcm43xx
```

I wish everyone good luck, and if you have anymore questions, just e-mail me at 
```
ii AT insaneinnovations.net
```
[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkRed"]-**"HEIL MEIN TEIL!!"** *Luther "Laz" D.(Me)*[/COLOR][/SIZE]

---

### Post by calum on 2007-01-19
> **webman2k said:**
> 3. Download the following file, and copy it to your desktop:
[http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o)

Note that it is quite possibly illegal to be making this file publicly-available, hence the reason the other tutorials tell you to use the fwcutter utility on your own OS X volume.

---

