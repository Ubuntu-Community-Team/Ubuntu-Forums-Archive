---
title: "Macbook Pro Santa Rosa: Network manager - someone got it working?"
date: 2008-05-09
forum: Apple Hardware Users
---

### Post by philipp. on 2008-05-09
Hello!

Is anyone with a macbook pro Santa rosa using the network manager for managing his network? What drivers are installed?

I dont like wicd and I cant do anything I could do with nm.

So which drivers are you using?

Ndiswrapper? Then which file from the apple dvd did you use?

I need help!


I am currently writing from Mac as I have destroyed my cable networ, too!!! :confused:


Hardy sucks! Everything was so nice with gutsy.... :(


Please please help me

Thank you very much!!!

---

### Post by cyberdork33 on 2008-05-09
depends on what version of Macbook Pro you are using. wicd has been recommended recently because something is broken with nm when using madwifi.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by khelben1979 on 2008-05-09
Try Debian instead.

---

### Post by philipp. on 2008-05-09
Both answers arent very satisfying for me:

cyberdork33, that was the point. I want to use network manager, cause it gives me the feeling to use a stable and modern operating system. And not wicd. I know that there are problems with madwifi, so I ask for the correct windows driver to use with ndiswrapper.

khelben1979, sorry I will not change my whole operating system to get my network working. And i do not even have a garantee for this.


My simple question is:
Does anyone use a Macbook Pro with network manager? And then: How? :)

Thanks in advance!

Some information that might be interesting:
```
$ lspci | grep Ath
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```

---

### Post by cyberdork33 on 2008-05-09
> **philipp. said:**
> cyberdork33, that was the point. I want to use network manager, cause it gives me the feeling to use a stable and modern operating system. And not wicd. I know that there are problems with madwifi, so I ask for the correct windows driver to use with ndiswrapper.
if you are using 63bit Ubuntu there are no 64bit Windows drivers.

if you use 32bit windows drivers, they are on your Leopard DVD and will be installed much the same way that the Broadcom drivers are installed for those with Broadcom hardware (like on the Macbook Air). Those instructions should help you through the process, though you have to use the atheros driver rather than the broadcom driver:
[https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7](https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7)

---

### Post by njpatel on 2008-05-10
> **philipp. said:**
> Hello!

Is anyone with a macbook pro Santa rosa using the network manager for managing his network? What drivers are installed?

So which drivers are you using?

Ndiswrapper? Then which file from the apple dvd did you use?


Yes, I use NetworkManager all the time with my Macbook Pro (santarosa). 

As mentioned, the madwifi drivers have some issues, so you definitely need to use ndiswrapper. I don't know where exactly to find these drivers, as I downloaded them off the internet (and don't have the link), but the driver I use is called:

net5416

I believe that it is part of the Atheros AR5416 driver package, so if you can find that, you've found your driver!

I hope that helps.

- Neil

---

### Post by d0b33 on 2008-05-10
I adapted the macbook air tutorial for my macbook 3,1 to install my driver
[https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7](https://help.ubuntu.com/community/Macbook_Air#head-146f51398e2debca46f8962a0c51dc0eee7a4ba7)

The driver installed correctly but I still could not get my wireless to work, hoping somebody can recommend a driver that worked for them

---

### Post by philipp. on 2008-05-10
I installed the driver you have mentioned from the Mac CD #1 that came with the macbook pro.  As in the tutorial. I have used 
net5416.inf

But it does not work. Not with the network manager and even not with wicd.

What can I do to have network connection?? :confused:
```

$ lspci | grep Ath
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
philipp@philipp-laptop:/$ ndiswrapper -l
net5416 : driver installed
        device (168C:0024) present (alternate driver: ath_pci)
philipp@philipp-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DSLWLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:CD:91:B9
          Bit Rate=54 Mb/s
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by sunbird on 2008-05-10
Very odd... I am using madwifi with network manager just fine on my Macbook Pro 3.1 (santa rosa). 

I didn't do anything -- clean 8.04 install followed by installing madwifi per the instructions on the macbookpro wiki page. I am not running ndiswrapper. Sometimes my connection drops, but otherwise, works fine.

And I have the same hardware:

```

$ lspci | grep Ath
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
```

Sorry I can't be more helpful.

---

### Post by philipp. on 2008-05-10
That sounds very strange...

When did you install 8.04? Was it a fresh installation or an upgrade?

How can I reinstall my ubuntu without loosing my configs and my installed apps?

Thanks!

One difference between our system I can see, is that I have 32 bit version installed and you 64 bit


So what would you all say? Investigate and eliminate the error or reinstall?

---

### Post by cyberdork33 on 2008-05-10
> **philipp. said:**
> I installed the driver you have mentioned from the Mac CD #1 that came with the macbook pro.  As in the tutorial. I have used 
net5416.inf

But it does not work. Not with the network manager and even not with wicd.

What can I do to have network connection?? :confused:
```

$ lspci | grep Ath
0b:00.0 Network controller: Atheros Communications Inc. AR5418 802.11abgn Wireless PCI Express Adapter (rev 01)
philipp@philipp-laptop:/$ ndiswrapper -l
net5416 : driver installed
        device (168C:0024) present (alternate driver: ath_pci)
philipp@philipp-laptop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DSLWLAN"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:CD:91:B9
          Bit Rate=54 Mb/s
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```According to your output, the card is active and working. Make sure that the card is in "roaming mode" in the Network configuration app in System > Administration > Network

---

### Post by philipp. on 2008-05-10
:KS:KS:KS

It works!! It wo-orks!:)

With network manager!!

The only thing I changed: I blacklisted the "ath_pci" driver in /etc/modprobe.d/blacklist

I am using the atheros driver from the MAC DVD. in the atherosxpinstaller.exe => net5416.inf


One thing to mention: When I said it is not working: I knew it was kinda working but I could not connect to a network. Always stuck in "configuring devices", so no connection established.

Thanks all! :mrgreen:
:KS:KS:KS

---

### Post by sunbird on 2008-05-10
I just did a fresh install after backing up my /home and /etc. I then rsynced my home directory and when I need a specific /etc file from my prior config, I copied it. It took me about a day to get all of my old apps installed and get my config how I like it, but everything runs pretty seemlessly now.

I think it must be something specific to your machine or your install because there would be more posts on the topic otherwise... but I don't really know. :\

---

### Post by philipp. on 2008-05-10
sunbird are u using madwifi drivers now?

I dont really want to reinstall my system

---

### Post by sunbird on 2008-05-10
Yes, madwifi. I followed [this wiki]("https://wiki.ubuntu.com/MacBookPro"). I'm sure you don't have to do a reinstall... there should be a way to make it work. Did you follow all of the instructions on the wiki? 

I'm mystified, but I'm a noob...

---

### Post by cyberdork33 on 2008-05-10
the ubuntu default version of ath_pci will conflict with the madwifi compiled module. you need to block the Ubuntu version by adding ath_pci to /etc/default/linux-restricted-modules-common

(and remove it from the blacklist file, otherwise it won't load either version.

---

