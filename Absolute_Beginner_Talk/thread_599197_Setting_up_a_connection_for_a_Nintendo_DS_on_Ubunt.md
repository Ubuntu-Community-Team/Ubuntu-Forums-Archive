---
title: "Setting up a connection for a Nintendo DS on Ubuntu - Without using a router"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Edgewalker_001 on 2007-11-01
I have a rather interesting problem... I want to connect a Nintendo DS to the internet by using my laptop as a wireless access point (I only need that one wireless connection) the laptop is connected to the internet via a standard wired connection, and has an installed wireless network card, so my question is, would it be possible for me to pull this off?

The reason for this is that the router I was previously using suffered a malfunction, and I need a temporary solution to remedy this situation.

Basically, I know that what I essentially need to do is bridge the two ethernet connections, and then configure the wireless card to connect to the DS, but I have absolutely no idea how to do this, and I am a beginner at using Ubuntu (and Linux)

However, the laptop does not contain anything important, and I suppose that any damage I might inadvertently cause can be repaired by a simple reformat.

Thankful for any and all help.

---

### Post by ofb on 2007-11-01
Does a DS just connect to the net like a regular computer? If so, this is simple Internet Connection Sharing, which is an easy option using Firestarter.

---

### Post by Edgewalker_001 on 2007-11-01
Well, as far as I know, it connects as a normal computer... But it has a slew of unusual complications that makes the actual connection a hassle.

Edit: Also Firestarter appears to be unavailable for download at the moment.

---

### Post by ofb on 2007-11-01
Okay, are you asking how to pass the internet through the laptop? That would be the ICS part. The laptop's wireless would be its connection to the LAN. So in typical ICS, both the laptop and the LAN computer (in this case the DS) would connect to the net through the laptop's wired connection. 

It's a common set-up for people with 2 computers and no hub or router.

If you're asking how to make the laptop's wireless card talk to the DS's wireless, that I can't help with since I'm still using cable. I imagine it must be similar to whatever you do with the DS to communicate with the router.

Re Firestarter - must be a hiccup at the repositories. It should be availabe soon enough.

EDIT: something to read while you wait
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

---

### Post by Edgewalker_001 on 2007-11-01
I have installed Firestarter, but for some reason it won't allow me to start the firewall since my wireless ethernet card "is not ready".

---

### Post by MaximusTG on 2007-11-01
You can do this, but only if your wireless card supports "soft-AP" mode (master mode it is called I believe?). You can setup ICS with an Ad-Hoc connection, but the DS won't connect to that. 

So you should search for a way to use your wireless card in master mode

---

### Post by Edgewalker_001 on 2007-11-01
Well, from where do you edit the settings for master mode?

---

### Post by MaximusTG on 2007-11-01
Well, first, which wireless card do you have?

Pleas post output of the 'lspci' command

---

### Post by ofb on 2007-11-01
Might help.
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by Edgewalker_001 on 2007-11-01
Well, as I said I am pretty green when it comes to Linux.

I have no idea how to use the Ispci command, but a quick look under the device manager reveals the card to be PRO/Wireless 2200BG Network Connection.

---

### Post by MaximusTG on 2007-11-01
Okay, well you already gave the name, so that's enough information
Did a quick search, and found this site:

[http://sourceforge.net/projects/ipw2200-ap](http://sourceforge.net/projects/ipw2200-ap)

It's a project for an AP-driver for the intel 2200BG wireless card, which would allow it to act like a wireless access point.
But you would have to install it yourself from source, and then route your internet through it..
IMHO you are better off picking up an old 11 Mbit WLAN router 2nd hand or something. Far easier, and you would have to turn it off anyway when you are done playing, because the DS only supports WEP encryption, and that's not much of a security measure anymore..

---

### Post by Edgewalker_001 on 2007-11-01
Well... Thank you and all that, it sounds great, but where is the link?

Edit: Oh, you already fixed it XD

---

### Post by ofb on 2007-11-01
For future reference, when someone says something like "post output of the 'lspci' command", open a terminal.

Menu -> System Tools -> Terminal

Type in: lspci

Hit return, and you'll get something like this,

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:04.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 SCSI storage controller: Adaptec AHA-7850 (rev 03)
00:0a.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
00:0b.0 Ethernet controller: 3Com Corporation 3c900B-TPO Etherlink XL [Cyclone] (rev 04)
00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440-SE] (rev a3)
```

That's the "output" that you're being asked to post.

---

### Post by Edgewalker_001 on 2007-11-01
Um... Slight problem, how do I install the driver?

---

