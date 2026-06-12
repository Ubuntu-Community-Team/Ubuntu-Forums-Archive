---
title: "iBook 12&quot; problem: no WiFi"
date: 2011-01-09
forum: Apple Hardware Users
---

### Post by unouwan2 on 2011-01-09
Greetings all,

after reading this [rave review]("http://lowendmac.com/ed/leeds/11al/i-love-ubuntu.html") of Maverick Meerkat on old mac, I decided to take the plunge. However, after the installation of 10.10, I can't get the wifi to work. it worked like a charm under OSX 10.4.

I'm a complete Ubuntu newb, so please bear with me. I don't know how to identify what the wifi chip is inside the iBook. I am connecting to an Apple Airport Extreme. My other macs and connect using WPA-PSK security, and everything just clicks into place after entering the network password.

Without the wifi I can't download any updates etc. I might be able to find an ethernet cable to tether the laptop if I need to download directly, but for now I"m hoping its just a matter of changing some settings or configurations to make it work.

The ubuntu system monitor reports that I have the following:
Release 10.10 (Maverick)
Kernel Linux 2.6.35-22-powerpc
GNOME 2.32.0

Hardware
Memory: 1.1 GiB
Processor: 7455, altivec supported

System Status
available disk space 48.1 GiB

under administration/network tools I am able to choose Wireless Interface (wlan0) in the Network Device popup, and I am able to enter the password in the configuration pane, but when I hit apply the exclamation point remains in the status bar's network connection symbol indicating no connection. This is all I am able to figure out how to do at this point.

Can anyone help?

THanks

---

### Post by unouwan2 on 2011-01-09
Spent some time searching the docs. installing b43-fwcutter worked.

---

### Post by danieru on 2011-01-12
I had the same symptoms as you for my iBook G3, but for me the problem was different. I don't have a broadcom card like you, my airport 802.11b card is, per wikipedia, a 're-branded Lucent WaveLAN/Orinoco Gold PC card'. No matter what I did, I couldn't connect to my network. Finally in OSX, I ran all the updates, and it brought the airport card's firmware from 8.7 to 9.52, and I was able to connect just fine after that. Perhaps it added support for WPA, I'm not sure, but it works!

---

