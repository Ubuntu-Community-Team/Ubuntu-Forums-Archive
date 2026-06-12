---
title: "Getting internet in Ubuntu"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by snoopy104 on 2006-07-30
Hi, i've just installed Ubuntu on one of my hard drives to see what all the fuss is about, I'm completely new to unix/linux.

I'm using a Texas Instruments 802.11g PCI card to connect to a Linksys WAG54G wireless gateway using DHCP. I'm not using any form of encryption (WEP/WPA) because i seem completely unable to get a connection when either is enabled regardless of how confident I am that it's set up correctly. So i'm using mac address filtering instead.

I guess i've become accustomed to Windows XP automatically detecting all the settings upon install?

On Ubuntu:

If I go into 'network settings' it appears that Ubuntu recognises that I have a wireless network card;

I have 'WLAN0', which is reported as being 'Active'

I have entered the ESSID correctly and tripple checked it.

The key type is set to 'Hexadecimal' as default

I have left the 'Wep Key' box empty, as i'm not using wep.

The configuration is set to DHCP

Despite this, I am unable to get online. I think the problem lies with the loopback adaptor 127.0.0.1 being the default?

i've been through all of the settings that I can find, but most stuff is greyed out and it doesn't appear that anything is even trying to establish a connection or configure an IP address??

When opening firefox, I can't get anywhere?

Any ideas?

Thanks.

---

### Post by snoopy104 on 2006-07-30
p.s. i'm using  v6.06

---

### Post by Village on 2006-07-30
I don't know if this will help but it might point you in the right direction. 

It could be that you need to install Ndiswrapper and then run the drivers of your wifi card though it? I'm was trying to do a similar thing with my wifi card. 

Hope this helps

---

### Post by snoopy104 on 2006-07-30
Thanks, but i'm a little confused about what Ndiswrapper is/ how to use it?

Is it something I need to download? or is it already part of ubuntu? how do I access it and how do I use it?

Sorry for being a rookie, I have only started using linux today.

I have done some web searches on it, but the pages I get seem to skip steps or not explain themselves in enough detail, probably fine for regular linux users, but a bit confusing for those of us migrating from windows..

thanks for the reply.

---

### Post by Village on 2006-07-31
I'm very new to this world to, and so I'm naturally nervous about given out advice as it could be wrong.

That said;

I think that Ndiswrapper basically allows you to run the drivers of windows software in Linux, I haven't used it myself (as currently I'm having my own Ubuntu related problems). I think that you have to extract the *.inf file, which I think is the driver information itself and then run it though Ndiswrapper. 

I hope that helps. Do some digging around on the Internet and you might find out some more info.

Village

---

### Post by Third Thoughts on 2006-07-31
The first thing you want to do is figure out exactly what card you have. Open up a terminal (Applications->Acessories->Terminal I believe) and type 
```
lspci
```
This will list all of the hardware/peripherals you've got installed. Look for Texas instruments and get the actual number of the card you've got. Then search this forum for any information about that card. If you can't find anything then post the output of the lspci command here and we'll try to help you.

~Andrew S.

---

