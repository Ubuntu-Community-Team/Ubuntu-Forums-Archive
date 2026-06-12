---
title: "WPA new iMac Problems"
date: 2008-06-16
forum: Apple Hardware Users
---

### Post by ninjapenguin on 2008-06-16
Hello I just installed Ubuntu on my new iMac, and I am trying to set up the wireless.  I got the broadcom driver installed through ndiswrapper, and I am able to view all of the signals around me.  The problem is my network has a WAP/WAP2 protection on it.  So I can try to connect to my network, but it just keeps asking for my username and password every so often and never connects.  When I turned off my protection I was able to connect to the router, but it went off sparatically.  That could be just because of outside interferrence, because I live in an apartment complex.  I have read there are some problems with connecting to WAP, and I was hoping some one has been able to do it and if so how they did it.

---

### Post by cyberdork33 on 2008-06-16
what windows driver are you using?

---

### Post by ninjapenguin on 2008-06-16
I am using the xp one for broadcom that came on the install cd.  I checked on ndiswrapper to make sure the driver was running and could find the device and it showed that the device was there.

---

### Post by cyberdork33 on 2008-06-16
> **ninjapenguin said:**
> I am using the xp one for broadcom that came on the install cd.  I checked on ndiswrapper to make sure the driver was running and could find the device and it showed that the device was there.
You might try the dell driver that is linked elsewhere.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

---

### Post by ninjapenguin on 2008-06-18
> **cyberdork33 said:**
> You might try the dell driver that is linked elsewhere.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

I ndiswrapper -r the apple version of the driver and tried the dell driver, but when i modprobed the ndiswrapper I got an infinite loop of statement lines, and had to do a hard restart.

---

### Post by cyberdork33 on 2008-06-18
> **ninjapenguin said:**
> I ndiswrapper -r the apple version of the driver and tried the dell driver, but when i modprobed the ndiswrapper I got an infinite loop of statement lines, and had to do a hard restart.
where did you get your ndiswrapper? from the repos? It sounds like you may have other issues that need to be resolved first... Seems strange anyway that you are getting many errors.

---

### Post by ninjapenguin on 2008-06-18
> **cyberdork33 said:**
> where did you get your ndiswrapper? from the repos? It sounds like you may have other issues that need to be resolved first... Seems strange anyway that you are getting many errors.

I got my ndiswrapper off of a link that was on one of the community documents for the MacBook Pro Santa Rosa I think, but I forgot that before I installed the Dell Version of the Driver I re-installed Ubuntu on my computer, because I had like 1.5 gigs of stuff in my trash that I couldn't empty because of permissions and I didn't know the sudo command to empty the trash.  My wireless works on my OS X and XP partition.  Also, I only show about 76% signal from my router while on Ubuntu, but 100% on XP and OS X.  So I have a feeling that there is probably something wrong with the ndiswrapper that I have, because it isn't configuring the broadcom driver correctly probably.

---

### Post by cyberdork33 on 2008-06-18
the signal strength always seems to be reported lower in Ubuntu. This is not unusual.

There seem to have been some issues with WPA recently. You might also try configuring the network manually in the system menu, or try using wicd instead of network-manager.

P.S. your trash is in /home/yourusername/.Trash. If you start a nautilus browser with sudo, you can navigate to that folder and delete anything you like.

---

### Post by ninjapenguin on 2008-06-18
> **cyberdork33 said:**
> the signal strength always seems to be reported lower in Ubuntu. This is not unusual.

There seem to have been some issues with WPA recently. You might also try configuring the network manually in the system menu, or try using wicd instead of network-manager.

P.S. your trash is in /home/yourusername/.Trash. If you start a nautilus browser with sudo, you can navigate to that folder and delete anything you like.

Thank you I wasn't sure exactly where the trash was, and whenever I get home I will try wicd instead of network-manager, but I might install kubuntu instead of ubuntu first, just to try it out and maybe it could just be a lil glitch on my ubuntu cd that isn't on my kubuntu.

---

### Post by ninjapenguin on 2008-06-19
I still have not gotten my WPA to work.  This is my wpa_supplicant.conf file:

network={
	ssid="Obel"
	proto=WPA
	key_mgmt=WPA-PSK
	psk=f631f1d60aeee81ef8a9786f9dd00faad9fced38889b7d580b756ba3db56067d
}

and when I tested it this is what I typed and got back:

obel@Linux-Ubuntu:~$ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w
Trying to associate with 00:1e:52:7c:62:c6 (SSID='Obel' freq=2452 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

If some one can please help me out it'd be much appreciated

---

### Post by jmallen2982 on 2008-06-22
If you're using Hardy then forget ndiswrapper, there's a much better solution:

Check this out:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

Apparently Hardy comes with a built-in Broadcom driver, but it doesn't work because it requires a firmware to function. This is VERY easy to install though. I know nothing about ndiswrapper. I tried to use it and luckily found out about the built-in driver. Get ride of ndiswrapper and whatever went with it and then click here:

[http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb](http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb)

It's a link to the debian package that contains the broadcom firmware. I don't really know exactly how it works, but it does. This includes WPA support. All I know is that I have an early 2006 iMac and I clicked on that link and I had WiFi. So make of that what you will.

---

### Post by hajk on 2008-06-23
> **jmallen2982 said:**
> If you're using Hardy then forget ndiswrapper, there's a much better solution:

Check this out:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

Apparently Hardy comes with a built-in Broadcom driver, but it doesn't work because it requires a firmware to function. This is VERY easy to install though. I know nothing about ndiswrapper. I tried to use it and luckily found out about the built-in driver. Get ride of ndiswrapper and whatever went with it and then click here:

[http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb](http://ubuntu.cafuego.net/pool/hardy-cafuego/broadcom/b43-firmware_1.0-0cafuego0_all.deb)

It's a link to the debian package that contains the broadcom firmware. I don't really know exactly how it works, but it does. This includes WPA support. All I know is that I have an early 2006 iMac and I clicked on that link and I had WiFi. So make of that what you will.Unfortunately, this is no solution for the Broadcom 4328 rev 05 wireless chip in the new iMac (or in any recent 2008 Apple Intel computer) as this chip does not use that firmware. Your own 2006 iMac contains an entirely different chip, not comparable at all (though it shares the Broadcom name, of course).

---

