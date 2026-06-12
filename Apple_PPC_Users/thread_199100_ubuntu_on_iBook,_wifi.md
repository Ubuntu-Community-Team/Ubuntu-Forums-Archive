---
title: "ubuntu on iBook, wifi?"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by logophobia on 2006-06-18
I really need wifi on my laptop (iBook G4), is it a good idea to put ubuntu on it? Will the airport extreme card work with the GNOME network manager / nsdiwrapper? Do nsdiwrapper and networkmanager work together (I don't want to connect to wifi w/ commandline)? Has anyone got it working? w/ WPA, TTLS/PAP support? Any directions would help greatly, thnx.

---

### Post by robino on 2006-06-18
You should be able to make wireless (airport extreme from broadcom) work, you can follow [this howto]("http://ubuntuforums.org/showthread.php?t=185174"). 

As I understood, not all functions work yet but using networkmanager should work to connect to open networks and wep.

I use an additional usb-stick based on a zd1211 chip that works out-of-the-box, and which I also use [succesfully ]("http://www.netstumbler.org/showthread.php?t=18159")in OSX (however not as good as in GNU/Linux, since speed is much lower in OSX)

---

### Post by maxmartin on 2006-06-18
I used the howto robino listed, and I've got my iBook G4's wireless working fine.

---

### Post by logophobia on 2006-06-18
Thank you. I really need authentication wpa w/ ttls/pap support for my university wireless network. Otherwise my iBook is pretty useless there. Any info on that?

---

### Post by robino on 2006-06-19
Ok, I just read that, as of last Saturday, the driver is fully integrated in the [new kernel]("http://lkml.org/lkml/2006/6/17/125"), so you can also upgrade to this kernel and/ or wait untill it will be fully integrated into Ubuntu.

Then, I just read a [very good and extensive HowTo ]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-4a3bf7f2ad33f5a02c8bb4f0ca4a74c9b884a841")on the webpage of the writers of the driver. It says that WPA *is* supported. 

Just follow those instructions to enable the driver with the current kernel. Although it does not say it [explicitly]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-27c9d2bcef176b1d0fd48be3bb437e1577ad6014"), I suppose networkmanager should work with WPA and airport extreme. Otherwise you can use wpa_supplicant.

I would say, try it, and report your results!!  :D

---

### Post by unconquerable on 2006-06-19
[QUOTE=robino]Ok, I just read that, as of last Saturday, the driver is fully integrated in the [new kernel]("http://lkml.org/lkml/2006/6/17/125"), so you can also upgrade to this kernel and/ or wait untill it will be fully integrated into Ubuntu.

Then, I just read a [very good and extensive HowTo ]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-4a3bf7f2ad33f5a02c8bb4f0ca4a74c9b884a841")on the webpage of the writers of the driver. It says that WPA *is* supported. 

Just follow those instructions to enable the driver with the current kernel. Although it does not say it [explicitly]("https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-27c9d2bcef176b1d0fd48be3bb437e1577ad6014"), I suppose networkmanager should work with WPA and airport extreme. Otherwise you can use wpa_supplicant.

I would say, try it, and report your results!!  :D[/QUOTE]

So that means that their IS a driver with ubuntu for the Airport Extreme card?  Will it work with out the changes listed above?

---

### Post by robino on 2006-06-19
Basically, the driver is *already* loaded in Ubuntu Dapper. You only need to enable the Firmware.

You enable the driver by loading the right Firmware. The following code should do the trick for you, according to the [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8") on the Ubuntu Wiki.

```
 
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

That's all to enable Airport Extreme in Dapper...

See for more information: [WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Then (reboot or) unload and reload the driver by ```
modprobe -r bcm43xx
modprobe bcm43xx
```

And a simple ```
sudo ifconfig eth1 up
```

makes your driver work...

**Read for more information how Wireless works in Dapper: the [Ubuntu Wifi Docs ]("https://wiki.ubuntu.com/WifiDocs")**

---

### Post by dearreid on 2006-06-19
I have an iBook G3 (500Mhz, Dual USB), with an original AirPort card (not Extreme, 802.11b only). I recently installed Ubuntu 6.06, in hopes of getting a little more life out of my trusty sidekick before breaking down and buying a new laptop.

I've scoured every corner of the web, including this forum, and haven't been able to find out if anyone has managed to get a similar setup working with WPA wireless security. I managed to get it to connect to an open network without a password, but can't seem to make it connect with WPA. The network in my building uses it, and the iBook is pretty much useless to me without that functionality.

I've installed network-manager-gnome and wpa_supplicant (although that was already there); I've tried wifi-radar and the wpa_gui. I've followed every big of advice I've found here, configuring .conf files and whatnot, but none seem to relate to my specific machine configuration. So far, I haven't even managed to get a pop-up menu in Network Manager to offer me the choice of a WPA connection.

Is there a wiki anywhere with start-to-finish instructions on making this work?

---

### Post by robino on 2006-06-20
[QUOTE=dearreid]I have an iBook G3 (500Mhz, Dual USB), with an original AirPort card (not Extreme, 802.11b only).

(...)

Is there a wiki anywhere with start-to-finish instructions on making this work?[/QUOTE]

According to what I [read about the driver airport.o]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Airport") which is used for your AirPort card (not Extreme, 802.11b only), there is *no* support for WPA unfortunately.

---

### Post by logophobia on 2006-06-20
[QUOTE=robino]
I would say, try it, and report your results!!  :D[/QUOTE]

Will do that. My last exams are in a couple of days, lots of free time after that :)

---

### Post by unconquerable on 2006-06-20
[QUOTE=robino]Basically, the driver is *already* loaded in Ubuntu Dapper. You only need to enable the Firmware.

You enable the driver by loading the right Firmware. The following code should do the trick for you, according to the [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#head-34d552a556ad5be07dbae4bafb73a6125139c9d8") on the Ubuntu Wiki.

```
 
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
```

That's all to enable Airport Extreme in Dapper...

See for more information: [WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

Then (reboot or) unload and reload the driver by ```
modprobe -r bcm43xx
modprobe bcm43xx
```

And a simple ```
sudo ifconfig eth1 up
```

makes your driver work...

**Read for more information how Wireless works in Dapper: the [Ubuntu Wifi Docs ]("https://wiki.ubuntu.com/WifiDocs")**[/QUOTE]


Is this possible to do when running Ubuntu from LiveCD, I wish to test out Airport Extreme compatibility before I take the plunge and erase OSX.

---

### Post by robino on 2006-06-20
[QUOTE=unconquerable]Is this possible to do when running Ubuntu from LiveCD, I wish to test out Airport Extreme compatibility before I take the plunge and erase OSX.[/QUOTE]

I should aways try the live-cd. It cost you nothing to try :) I can't remember if AE was working out of the box with the live cd however. But it will surely work when installed, and u follow the userguides. I don't know if you can follow this process when you are in a live system, but maybe you can try since it will not hurt anyone :cool: 

By the way, from a user experience, I never ditched OSX. I did a clean install a year ago with Gentoo (another distribution) and during the installation process I manually created 1 extra HFS(plus) partition mend for OSX. 

Reinstalling OSX doesn't take so much time. It just means half an hour extra work to install both Operating Systems. But don't forget the extra partition by manualling editing the partition table.

The only 'pain' is that when you reboot after reinstalling OSX, it will automatically reboot into OSX. But you can change this by booting into Ubuntu by holding the control key when booting (the firmware boot-menu will show up) and reconfigure yaboot.

---

### Post by cmorgan47 on 2006-10-24
i use the airport--not extreme--but from the liveCD it did not work.  did work once installed.  i took the plunge anyways cause 1) didn't care that much if i had to go back and 2) read similar reports here.

i understand that airport extreme is a different story and typically does not work out of the box, though it seems simple enough to make it work.  just commenting that the liveCD sometimes does not fully prove what will or will not work.

---

### Post by gautinad on 2007-01-01
hello all  
[Buick](http://twelvemonths.org/auto/auto1/index.html)

---

### Post by cihocvo on 2007-01-20
Hi 
[tramadol](http://tramadol.twelvemonths.org/index.html) 
[http://tramadol.twelvemonths.org/index.html](http://tramadol.twelvemonths.org/index.html) 
<a href=http://tramadol.twelvemonths.org/index.html>tramadol</a>

---

### Post by mwo on 2007-03-07
Hi @ll,

I have got an Ibook G4 running Edgy on it. Although it is written in German language I would like to recommend the following very useful URL for this Broadcom-WLAN-WPA-Topic: [http://ubuntu.macvillage.de/](http://ubuntu.macvillage.de/).

Please allow to summarize the main steps:

1.) I use the gnome-networkmanager application to connect to WLANs.
2.) sudo apt-get install bcm43xx-fwcutter
3.) Now the networkmanager will show you the applicable WLANs.
4.) Click on your WLAN and wait until your password request is prompted. Due to an application bug you cannot simply enter your password for you WLAN.
5.) Instead, open a terminal and type: wpa_passphrase <<your ssid>>
6.) Enter your password and press enter.
7.) Copy the passphrase to your password request and connect to your network.

That was the way it worked for me. Hope this may help.

Cheers,
Markus

---

### Post by fuoco on 2007-03-10
Thanks for the trick, it worked for me after much trying...
I assume this is related to bug [https://launchpad.net/ubuntu/+source/network-manager/+bug/52922/](https://launchpad.net/ubuntu/+source/network-manager/+bug/52922/) ?

Too bad this is not yet fixed even in feisty...

---

### Post by ditsch on 2007-03-10
> **fuoco said:**
> Thanks for the trick, it worked for me after much trying...
I assume this is related to bug [https://launchpad.net/ubuntu/+source/network-manager/+bug/52922/](https://launchpad.net/ubuntu/+source/network-manager/+bug/52922/) ?

Too bad this is not yet fixed even in feisty...

You are right, this is due to this bug. Markus, many thanks for translating my instructions into English, I am not looking into the forums that often :rolleyes:

---

### Post by dempzxtsds on 2007-03-12
Spam.

---

### Post by demtabletki on 2007-03-13
Spam.

---

### Post by oxempilzx on 2007-03-13
Spam.

---

### Post by demtabletkiq on 2007-03-14
Spam.

---

