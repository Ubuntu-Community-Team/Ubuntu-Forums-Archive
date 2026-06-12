---
title: "Back to try again"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by bfckarlos on 2007-01-16
I tried using Ubuntu a year or so back whilst at uni, but for some reson couldn't get my modem to configure, thereby no net access. This was a bit frustrating at the time and no matter what I tried, it didn't work though learnt a bit trying at the time, but would still say I'm a bit new to Linux scene.

Anyway I'm back to give it another go. I just downloaded the latest version 6.10 and ready to do a dual boot install with XP. But the situation has now changed regarding modem, I now have wireless router at home. Therefore what I'm after is any advice on issues that might arise with setting up the home network, as I seen a couple of threads highlighting difficulties doing this. However it'll be easier this time as I'll be able to use my works Xp laptop for research etc.

Any advice would be greatly appreciated.
Thanks

---

### Post by xyz on 2007-01-16
Depending on your specs,card...you may want to have a look at this:
[How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy]("http://ubuntuforums.org/showthread.php?t=185174")

---

### Post by bfckarlos on 2007-01-16
> **xyz said:**
> Depending on your specs,card...you may want to have a look at this:
[How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy]("http://ubuntuforums.org/showthread.php?t=185174")
  

Thanks for the reply, will have a browse through it. Actually it's a Netgear usb router and dongle. Not in front of it at the moment, but will have look later on and try some time soon to get it up and running.

---

### Post by bfckarlos on 2007-01-16
I also see that Linux not very happy with ATi Cards, oh dear. 

I now have pcie x1300  card in it, is that gonna make things worse for me. ](*,)

---

### Post by ljpm on 2007-01-16
> **bfckarlos said:**
> I also see that Linux not very happy with ATi Cards, oh dear. 

I now have pcie x1300  card in it, is that gonna make things worse for me. ](*,)

ATI cards work, it just may take a little more effort to get the more advanced features working.

[HTML]http://ati.de/support/driver.html[/HTML]

---

### Post by jvc26 on 2007-01-16
I run a slightly older 9800Pro AGP ATi card and thats not been too problematic for me, so you should be ok :) might just take a little bit of work to get up and running.
Il

---

### Post by bfckarlos on 2007-01-17
Thanks again for the help guys/gals I'm almost certain to install this coming weekend, so I'll probably be back.

---

### Post by doerum on 2007-01-17
Is there any encryption (WPA) on the wifi? In that case try to search forums for wpa. 

If not, i would probably download the driver (and then use nwdiswrapper (spelling error?) for installing). Check out synaptic and install Wifi-Radar or Networkmanager Gnome. 

Hoping some of this is useful.

---

### Post by CroEragon on 2007-01-17
ATI relesed recently new drivers for range of their cards. It is Crystal 7.1 and it resolved my 3d rendering issue on Radeon XPress 200. It may help you if you have problems.

---

### Post by Frank Golden on 2007-01-17
> **CroEragon said:**
> ATI relesed recently new drivers for range of their cards. It is Crystal 7.1 and it resolved my 3d rendering issue on Radeon XPress 200. It may help you if you have problems.I havn't heard of Crystal 7.1. As far as I know the latest drivers for ATi cards (Linux) is 8.33.6 available from

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

With instructions for Ubuntu dapper and Edgy. Use the 2nd method in either flavor
of Ubuntu. Follow directions carefully.

You may have native support for your Wi-Fi try that first. Native support is preffered over ndiswrapper. Ndiswrapper will work but can be dicey.

---

### Post by Frank Golden on 2007-01-17
> **CroEragon said:**
> ATI relesed recently new drivers for range of their cards. It is Crystal 7.1 and it resolved my 3d rendering issue on Radeon XPress 200. It may help you if you have problems.I havn't heard of Crystal 7.1. As far as I know the latest drivers for ATi cards (Linux) is 8.33.6 available from

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

With instructions for Ubuntu dapper and Edgy. Use the 2nd method in either flavor
of Ubuntu. Follow directions carefully.

You may have native support for your Wi-Fi try that first. Native support is preffered over ndiswrapper. Ndiswrapper will work but can be dicey.

Check out Automatix2 after you get Ubuntu set up and are comfortable with it.
It is a neat script to automate install of some programs not available in Synaptic.
It will install things like GoogleEarthLinux, restricted audio/video codecs needed to play
movies and MP3, WMA files etc. Warning installing some of these codecs is illegal in the USA. As a matter of fact you have to acknowledge this every time you fire up Automatix2.
You can get needed Firefox pluging here as well. Also available from Automatix2 is NetworkManager which allows you to configure your Wi-Fi for WPA if needed.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

