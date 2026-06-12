---
title: "Macbookpro5,5 and ubuntu 10.10"
date: 2010-11-29
forum: Apple Hardware Users
---

### Post by breimer273 on 2010-11-29
Hello,

I was once a user of Ubuntu on my macbook pro but it was very annoying not having WPA support on my wireless card. I searched on google but didn't really find anything saying how well the out of box support is for the macbookpro5,5. I am wanting to start using Ubuntu again but I really need full support or at least something that will be fairly simple or at least possible to get up and fully running.

Thanks,
Bill

---

### Post by smoors on 2010-11-29
Hi!

Works fine here with the wicd network manager. I had some issues with the default network-manager, but after removing it wicd worked nicely.

---

### Post by lael on 2010-11-29
What wireless card do you have?

```
lspci -nn
```
Mine yeilds:
```
$ lspci -nn |grep 802.11
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```

---

### Post by breimer273 on 2010-11-29
> **lael said:**
> What wireless card do you have?

```
lspci -nn
```
Mine yeilds:
```
$ lspci -nn |grep 802.11
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
```
I get the following:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```
I have gone ahead an installed 10.10 but even with the proprietary drivers I am not able to connect to my network. My network has WEP security but when I try to connect I get a bad password error. I know I am inputting the correct password and I am using the WICD network manager rather than the default. Thanks for the help.

---

### Post by breimer273 on 2010-11-29
[IMG]http://picasaweb.google.com/lh/photo/BAHYUkRSVdTlMK9P4HSUPQ?feat=directlink[/IMG]
[http://picasaweb.google.com/lh/photo/BAHYUkRSVdTlMK9P4HSUPQ?feat=directlink](http://picasaweb.google.com/lh/photo/BAHYUkRSVdTlMK9P4HSUPQ?feat=directlink)

I wanted to add a little more info to my problem above. The picture you can see is how I have my security setup on my laptop with the key entered. So if there is something wrong with how I have it set up on there please let me know. Otherwise I am out of ideas. Again thanks for the help! :D

---

### Post by smoors on 2010-11-30
> **breimer273 said:**
> I get the following:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```I have gone ahead an installed 10.10 but even with the proprietary drivers I am not able to connect to my network. My network has WEP security but when I try to connect I get a bad password error. I know I am inputting the correct password and I am using the WICD network manager rather than the default. Thanks for the help.

Hi! 

I've got exactly the same card and WPA and WEP are working fine here, even when relocating fast (walking through my university :D ). I have just looked at your screenshot and compared it with my settings, it's all the same.. Despite the fact that i'm using static ip addresses, but that should not bring up "bad password" errors. Have you double-checked the password?

---

### Post by breimer273 on 2010-12-01
> **smoors said:**
> Hi! 

I've got exactly the same card and WPA and WEP are working fine here, even when relocating fast (walking through my university :D ). I have just looked at your screenshot and compared it with my settings, it's all the same.. Despite the fact that i'm using static ip addresses, but that should not bring up "bad password" errors. Have you double-checked the password?

Hmmm well it seems that my problem was the fact that I was using WICD for my network manager. :P now that I am using the default with the STA driver available on the System->Administration->additional drivers everything is working fine. I will mark this as solved. Thanks for the help guys.

---

