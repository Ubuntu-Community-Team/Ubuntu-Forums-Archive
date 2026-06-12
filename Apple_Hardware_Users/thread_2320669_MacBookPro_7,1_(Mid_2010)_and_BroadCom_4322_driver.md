---
title: "MacBookPro 7,1 (Mid 2010) and BroadCom 4322 driver"
date: 2016-04-16
forum: Apple Hardware Users
---

### Post by maury2 on 2016-04-16
Hi all!! 

I'm a Ubuntu User from Ubuntu 6 but, believe me, I have never had so much trouble.

I have a MacBookPro 7,1 (Mid 2010) with Wireless BroadCom bcm4322, i installed its driver but i can't see any SSID.

I don't want to use Ethernet.

I tried with Additional Driver, install from Terminal bcmwl-kernel-source, firmware-b43-installer and Legacy version, compile from STA Driver source and ndiswrapper but without results.

Until Ubuntu 12 (maybe 11) Wireless works perfectly! Now, probably with new kernel 4, it seems there's no solution for this problem.

A PC, or Mac, or anywhere, without Internet, is unusable!!! Specially for me!!! 

I tried also with Mint, thought it's based on Ubuntu. An example of my problem is reported in this pic:
[IMG]http://s22.postimg.org/8gx0icypt/Screenshot_at_2016_04_16_10_33_08.png[/IMG]

Thanks and sorry for my english!!

---

### Post by Hadaka on 2016-04-16
Hi Broadcom does not have a wifi card BCM 4322, please verify your wifi card.
COPY and paste then post the output of,,
```
lspci -n | awk '/0200|0280/{print$3}'
```
thanks.

---

### Post by dellboy56 on 2016-04-18
hello there maury2 Welcome to linux i see your having a problem with your macbook pro luckily i can help you as i have the same macbook and use ubuntu and your using linux mint! anyways what you need to do is grab your cd that you installed mint on and if you look under pool then go to first folder search for a thing that says D Press that then install dkms then once thats done go back to pool folder then theres a restricted folder click that then you will see the bcm4322 driver click that and you will have Wireless :D hope it helped you if you have any concerns please reply back and ill try to help you have a good day:)

---

### Post by maury2 on 2016-04-22
@Hakada

the output is

14e4:432b
14e4:1684

and the Additional Driver Window reports "Broadcom Corporation: BCM4322 802.11a/b/g/n Wireless LAN Controller (Airport Extreme)"

@dellboy56

thanks for your advice! But your procedure is for install the drivers! Netherless i tried anyway!

I don't have a problem with driver installation but with the functioning of the driver! i cant see any ssid....

I tried today with ubuntu 16.04, specially for the new kernel, but it's seems no change

---

