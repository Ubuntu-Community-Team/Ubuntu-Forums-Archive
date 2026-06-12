---
title: "[howto] enabling wireless on 9.10"
date: 2009-10-09
forum: Apple Hardware Users
---

### Post by SaiHayashi on 2009-10-09
Hi all,

this is for those who installed 9.10 or kernel 2.6.3x and found their broadcom 43xx wireless chips unusable.  this is probably due to your wireless chip is not supported by the new b43 drivers.

i installed 9.10 64-bit on my macbook 4,1 with broadcom 4328 chip which is classified as unsupported according to [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")
the following is the steps I took to get my wireless working.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
comment out "blacklist bcm43xx"
go to System->Administration->Hardware Drivers
you should be able to see "Broadcom STA wireless driver", enable the driver and wireless is in your hand again.

This might sound a bit dodgy because i simply scrapped b43 drivers, but hey, old but works is nevertheless better than new but doesnt work.
please reply whether this "solution" works for you or not, although i may not be able to provide further solutions (since i dont know much about kernels).

cheers,
Sai

---

### Post by rifak on 2009-10-11
i have a macbook 3,1 with 4328 chip and my wireless worked fine after i did all of the updates after a fresh install. after the updates were completed, i did a restart, and the Broadcom STA Wireless driver was available. also, i never had to comment out 'blacklist bcm43xx' in /etc/modprobe.d/blacklist.conf

the only weird thing about it is when i check the Connection Speed under Network Manager's Connection Information, it's showing weird speed changes. One second it will be at 57 Mbps, and then it will go to 7 Mbps, then to 44 Mbps. im not sure what is causing this (because on my other ubuntu computer isn't showing this change), so im not sure if my connection really is fluctuating, or if its a problem with the driver.

---

### Post by SaiHayashi on 2009-10-11
> **ego-sum-deus said:**
> i have a macbook 3,1 with 4328 chip and my wireless worked fine after i did all of the updates after a fresh install. after the updates were completed, i did a restart, and the Broadcom STA Wireless driver was available. also, i never had to comment out 'blacklist bcm43xx' in /etc/modprobe.d/blacklist.conf

the only weird thing about it is when i check the Connection Speed under Network Manager's Connection Information, it's showing weird speed changes. One second it will be at 57 Mbps, and then it will go to 7 Mbps, then to 44 Mbps. im not sure what is causing this (because on my other ubuntu computer isn't showing this change), so im not sure if my connection really is fluctuating, or if its a problem with the driver.
i think connection information displays real-time connection speed. it is normal to observe a sudden drop and rise of wireless connection speed, as many environmental interference can affect it. but im interested to hear ur 4328 chip works out of the box.  can i ask u to confirm that u are using b43 drivers and not bcm43xx?  hmm... i wish i could test more thoroughly but i havent had the guts and time to reinstall a beta before official release.

---

### Post by rifak on 2009-10-11
im pretty sure im using b43 driver. in /etc/modprobe.d/blacklist.conf it says my bcm43xx is blacklisted and replaced by b43 and ssb. also, maybe this is where it doesn't make sense, when i issue a 'lshw -C network' command, it shows that my driver=wl0. and under Network Manager's Connection information, it shows that the driver is wl. is there another way to check?

---

### Post by cyberdork33 on 2009-10-11
> **ego-sum-deus said:**
> im pretty sure im using b43 driver. in /etc/modprobe.d/blacklist.conf it says my bcm43xx is blacklisted and replaced by b43 and ssb. also, maybe this is where it doesn't make sense, when i issue a 'lshw -C network' command, it shows that my driver=wl0. and under Network Manager's Connection information, it shows that the driver is wl. is there another way to check?
wl is the proprietary driver that has been provided by broadcom. bcm43xx is OLD and probably should not be used if you can get away with it. b43-legacy is the version of the b43 driver for older "unsupported" hardware.

---

### Post by rifak on 2009-10-11
> **cyberdork33 said:**
> wl is the proprietary driver that has been provided by broadcom. bcm43xx is OLD and probably should not be used if you can get away with it. b43-legacy is the version of the b43 driver for older "unsupported" hardware.

so am i using the correct/newest driver then?

---

### Post by amd-64 on 2009-10-12
Once I recompiled wl, all stability problems were gone. 

[http://forum.notebookreview.com/showthread.php?t=418403#wireless](http://forum.notebookreview.com/showthread.php?t=418403#wireless)

---

### Post by rifak on 2009-10-12
> **amd-64 said:**
> Once I recompiled wl, all stability problems were gone. 

[http://forum.notebookreview.com/showthread.php?t=418403#wireless](http://forum.notebookreview.com/showthread.php?t=418403#wireless)

thanks for that. im not sure if i wanna go through with recompiling because i dont think the stability of the signal is anything to do with my driver...i think its with my shi**y home wireless router. i think this because when im on my schools network, the signal strength/stability is constant. also, the b43 driver isn't loaded, and the wl driver is for sure loading, so i think im set.

---

### Post by rifak on 2009-10-12
i can confirm that my wireless stability has nothing to do with the driver. i went out today and bought a new wireless router and the problem is fixed.

---

### Post by Cerin on 2009-11-06
> **SaiHayashi said:**
> Hi all,

this is for those who installed 9.10 or kernel 2.6.3x and found their broadcom 43xx wireless chips unusable.  this is probably due to your wireless chip is not supported by the new b43 drivers.

i installed 9.10 64-bit on my macbook 4,1 with broadcom 4328 chip which is classified as unsupported according to [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")
the following is the steps I took to get my wireless working.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
comment out "blacklist bcm43xx"
go to System->Administration->Hardware Drivers
you should be able to see "Broadcom STA wireless driver", enable the driver and wireless is in your hand again.

This might sound a bit dodgy because i simply scrapped b43 drivers, but hey, old but works is nevertheless better than new but doesnt work.
please reply whether this "solution" works for you or not, although i may not be able to provide further solutions (since i dont know much about kernels).

cheers,
Sai

Thank you thank you thank you! I have a MacbookPro5.5, and none of the guides in this forum work with setting up wireless, except yours! The b43 driver fails. The wl driver fails. But the old "horrible" bcm43xx driver works perfectly.

---

### Post by Cerin on 2009-11-08
The only caveat I've found with the bcm43xx module is that it's considerably slower and more unreliable then the equivalent driver in OSX. On the Mac side, it'll connect to a wireless network within a couple seconds, but in Linux, it'll can take several minutes. Still, it's better than nothing. I'll probably retry the b43 and ssd modules in a few months after the bugs have been ironed out.

---

### Post by Geocron on 2009-11-09
[COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if you dont see b43 driver u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

---

### Post by rifak on 2009-11-10
ive found that the connection stability is only with WPA/WPA2 networks. i have a bcm4328 network card and had HORRIBLE connection issues. i would have to constantly disconnect, then reconnect, to keep a good flow of internet. my home network had wpa2 security and this was what was causing the problems. i recently changed it to wep and the stability is perfect...no losses of connection. so, it may be with how the driver handles wpa/wpa2 connections

---

### Post by eaglehacker on 2009-11-10
> **SaiHayashi said:**
> Hi all,

this is for those who installed 9.10 or kernel 2.6.3x and found their broadcom 43xx wireless chips unusable.  this is probably due to your wireless chip is not supported by the new b43 drivers.

i installed 9.10 64-bit on my macbook 4,1 with broadcom 4328 chip which is classified as unsupported according to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
the following is the steps I took to get my wireless working.

```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` [COLOR=Red]comment out "blacklist bcm43xx"[/COLOR]
go to System->Administration->Hardware Drivers
you should be able to see "Broadcom STA wireless driver", enable the driver and wireless is in your hand again.

This might sound a bit dodgy because i simply scrapped b43 drivers, but hey, old but works is nevertheless better than new but doesnt work.
please reply whether this "solution" works for you or not, although i may not be able to provide further solutions (since i dont know much about kernels).

cheers,
Sai

What does comment out mean? (highlighted in red above)
Sorry this is such a noob question.

Cheers,
--Eaglehacker

---

### Post by rifak on 2009-11-10
commenting out means that you put a symbol at the beginning to let the reader know not to read and execute that line...in this case, you will put the pound sign at the beginning of that like (#)...so like this:

it looks like this to start with:
```
# replaced by b43 and ssb.
blacklist bcm43xx
```

and after you are done editting with the comment, it will look like:
```
# replaced by b43 and ssb.
#blacklist bcm43xx
```

---

### Post by rocuan on 2009-11-11
> **Geocron said:**
> [COLOR=Red]TRY THIS BEFORE ANY OTHER METHOD [/COLOR]
i have a broadcom wifi card
i find that the wifi does not work with a fresh install EVEN if the card is RECOGNIZED 
to fix this this all i do is pug in a Ethernet cable (with internet on it) and up date
then go to the System>administration>Hardware drivers 
and activate the b43 driver (if you dont see b43 driver u probably don't have a broadcom)
then update again (by going to  System>administration>Update manager)
after that i can see wifi points and get on them 

[COLOR=Red]i recommend that you TRY THIS BEFORE ANY OTHER METHOD [/COLOR]

you my friend are a man among boys!! 
THANK YOU
many many hours of googling, hacking & pulling hair till i saw this :D
now everything is gravy

Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
Compaq Presario POS f700

---

### Post by Cerin on 2009-11-12
I've noticed wireless refuses to connect or save passwords after Hibernation, which effectively make Hibernation useless on a laptop.

---

### Post by edwinava1964 on 2010-05-20
I am on top of the world ! After reading this tread which is meant for Mac but I am having an Acer 2920Z laptop and now my wireless works after using the STA driver... after the installation and a restart.

Thanks Ubuntu Forum !

I was having Ubuntu 9.02 a while ago, the sound was not working,
now with 9.10, the sound is working and the wireless is working... Well done Ubuntu community ! .... although I am a Windows Vista user... but I do use linux in my work place...... well .... they have their places... :-):popcorn:

---

