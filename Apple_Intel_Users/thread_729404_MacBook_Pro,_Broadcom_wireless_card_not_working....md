---
title: "MacBook Pro, Broadcom wireless card not working..."
date: 2008-03-19
forum: Apple Intel Users
---

### Post by amaragon on 2008-03-19
Hi everyone,

Did someone with the same problem got the wireless card working??? I just got a new MacBook Pro and it comes with a Broadcom wireless card:

$> lspci -v | grep Broadcom0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)

I downloaded the latest release of ndiscwrapper, built it, installed it and I followed the directions in 

[https://help.ubuntu.com/community/WifiDocs/Driver/%20bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/%20bcm43xx/Feisty_No-Fluff)

with no success. Any comments? Suggestions???

I looked in the Mac OS DVD for a driver but I only found .exe files so I couldn't extract the .inf file.

Thank you all

aa

---

### Post by cyberdork33 on 2008-03-19
you have to use the driver on the leopard dvd. It is contained in one of the exe files. I think it is called xpinstaller.exe

[http://ubuntuforums.org/showthread.php?t=728530](http://ubuntuforums.org/showthread.php?t=728530)

---

### Post by amaragon on 2008-03-19
I actually did the same thing but with the other installer (they have 3 of them in the dvd). So I guess I was using the one for vista, called bcmwl6.inf.

Well, I used the xp and worked fine. Thanks for the link. Now to the sound problem. Do you know by chance how to fix this?

aa

---

### Post by DrAma999 on 2008-03-20
> **amaragon said:**
> I actually did the same thing but with the other installer (they have 3 of them in the dvd). So I guess I was using the one for vista, called bcmwl6.inf.

Well, I used the xp and worked fine. Thanks for the link. Now to the sound problem. Do you know by chance how to fix this?

aaYou just need to follow the wiki about MacBook Pro on the wiki page of ubuntu.

---

### Post by cyberdork33 on 2008-03-20
> **DrAma999 said:**
> You just need to follow the wiki about MacBook Pro on the wiki page of ubuntu.
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

---

### Post by amaragon on 2008-03-20
That is incorrect. I actually followed that page in the beginning and then I messed (by mistake) with the Madwifi drivers.

I think that page needs to be updated. I got the Mac two days ago, it is a last generation MacBook Pro with Intel Core 2 Duo 2.4GHz. This machine came with a Broadcom wireless card, and as you know the Madwifi is only for Atheros.

aa

---

### Post by DrAma999 on 2008-03-20
> **amaragon said:**
> That is incorrect. I actually followed that page in the beginning and then I messed (by mistake) with the Madwifi drivers.

I think that page needs to be updated. I got the Mac two days ago, it is a last generation MacBook Pro with Intel Core 2 Duo 2.4GHz. This machine came with a Broadcom wireless card, and as you know the Madwifi is only for Atheros.

aa

Just for the audio....I have your same model..following the wiki i fixed the audio

---

### Post by amaragon on 2008-03-20
Did you manage to get the Fn key working???

aa

---

### Post by DrAma999 on 2008-03-20
> **amaragon said:**
> Did you manage to get the Fn key working???

aa

Sure:)...find out how?...just following the wiki.. [https://help.ubuntu.com/community/MacBookPro#head-4c78243fc391cbf133a2668705dcab84d7017940](https://help.ubuntu.com/community/MacBookPro#head-4c78243fc391cbf133a2668705dcab84d7017940) :lolflag::lolflag:

---

### Post by amaragon on 2008-03-20
There is nothing there on how to fix the Fn key! :(

---

### Post by DrAma999 on 2008-03-20
Pommed is a daemon to support extra keys on apple computers. These include the brightness, eject, volume and others. Releases of Pommed 1.8 or up fully support the MacBook and MacBook Pro keyboards. It can be installed with this command:

sudo apt-get install pommed

You can check your pommed version number with this command:

pommed -v

[B]The default behavior on Apple keyboards is to have the top row keys primarily function as media keys (brightness, volume, etc), and have the expected function keys (F1, F2, etc) accessible with using the fn keys.

To reverse this behavior, edit the pommed configuration file with this command:

sudo gedit /etc/pommed.conf

Change the value of fnmode to "2", and save. At any time, you can change this value back to "1" to return to the default behavior. [/B]

---

### Post by amaragon on 2008-03-20
so??? that still doesn't fix the fn key. It just gives a different behavior for pommed, which is working for sure since the eject key works fine.

---

### Post by cyberdork33 on 2008-03-20
> **amaragon said:**
> There is nothing there on how to fix the Fn key! :(
he linked directly to the Fn key section. If that is not working for you then there is another issue. I think there may have been a bug report about this.

---

