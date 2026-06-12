---
title: "Wireless Networking with USB stick"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by DavidPM on 2006-10-07
Hi all,

It's my first post after downloading and installing ubuntu on another machine.

I've starting having a hunt around for information about LINUX systems as this is my first real endeavour into the LINUX world!

The knowledge gaps are immediately clear now, as I could setup wireless on XP but now have no idea where to start!

I've had a look at the networking admin page but my wireless device does not show up on the list. The helpdoc says this for those who cant see the device 'see need to set up wiki link to move forward with driver'...

( [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking) )

I'm not quite sure what that means as it doesn't point anywhere...

I've got a USB Belkin wireless receiver...

Does anyone know how I would go about doing this?

Many thanks

---

### Post by DavidPM on 2006-10-07
Further to this, I found this at  [http://www.linuxemporium.co.uk/products/wireless/#pid81766](http://www.linuxemporium.co.uk/products/wireless/#pid81766)

Recently, Belkin have changed the chip set on the USB stick, unfortunately they haven't changed the part or version numbers, so short of opening every box we have no means of checking what they have shipped to us. They are identifiable from the FCC ID on the stick itself: K7SF5D7050A has the rt2500 chip set, K7SF5D7050B the rt73. If you want to use the USB stick on most Linux systems, you will have to build the appropriate module against your kernel using the rt2570 or rt73 driver sources (which are included on the CD we provide with your wireless card) and be prepared to do some serious work to get it running. In some cases you may not succeed, for example people have experienced problems with 64 bit systems. We hope to be able to publish a HOWTO soon, and if you have any helpful advice, please let us know, but more importantly feed it back to the rt2x00 project.

I have a USB wireless device F5D7051 - Talk about baptism of fire!

---

### Post by AndyCooll on 2006-10-07
I too have Belkin USB Wireless sticks which require RT2570.

I used this thread to set mine up: [ HOWTO: Ralink RT2570 usb wireless driver]("http://www.ubuntuforums.org/showthread.php?t=106846")

On the Wireless Support forums [Wireless Support Forum]("http://www.ubuntuforums.org/forumdisplay.php?f=139"), Lambert (who wrote that HOWTO) is quite an active member ...at least he was the last time I visited!

:cool:

---

### Post by DavidPM on 2006-10-07
Thanks for your response but..

I've been stuck at square one for hours. It seems that these wireless tutorials don't assume new complete beginners but setting up the Internet is the first thing you do with these systems, anyhow..

sudo apt-get install cpp gcc build-essential linux-headers- `uname -r`

gives me...

Package cpp is not available
E: Package cpp has no installation candidate

same for gcc, build-essential if I do them individually.

How do I get this to work without my Ubuntu being connected to the Internet?

Many thanks

---

