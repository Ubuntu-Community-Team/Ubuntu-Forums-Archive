---
title: "Automatix can't install?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-29
Does anyone know if / how I can install Automatix in Breezy?

The reason I ask is because I cannot seem to get the current java to install, and I need it to be able to install my bible software that I use for school... 

Dapper and edgy do not work with my wireless card, so I have to stick with Breezy...

---

### Post by KingBahamut on 2006-11-29
Refer here, please.

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

### Post by Papa-san on 2006-11-29
So, basically, I am scrooged?

What a pity... I hate windoze...

---

### Post by taurus on 2006-11-29
Either upgrade to Dapper or install Edgy!  It's not the end of the world...

---

### Post by Papa-san on 2006-11-29
As I stated in my first post, I have excessive problems with both of those... Dapper requires a LOT of re-configuring to get my wireless to work, and I am still left with an un-fixable problem with my video driver that locks my system every hour or two...

Edgy seems to make the use of my wireless impossible. (I tried every how-to and thread I could find to fix it, but managed to bork four clean installs in a row, with no success...

---

### Post by Titus A Duxass on 2006-11-29
You are not scrooged (interesting usage), you have to do things manually.
What are you trying to install?

---

### Post by KingBahamut on 2006-11-29
Hardware devices and configuration please? 

I will try to help as best I can.

---

### Post by Papa-san on 2006-11-29
I am using a Dell lattitude C-610.
lshw:
```
 *-network:1
                description: Wireless interface
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@02:03.0
                logical name: wlan0
                version: 02
                serial: 00:90:4b:2c:52:6b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper ip=192.168.2.45 
```
and```
 *-display
                description: VGA compatible controller
                product: Radeon Mobility M6 LY
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:fcff0000-fcffffff irq:11

```I am not sure what else you might need to know, except that the biggest problem with this computer is the defective part that is between the keyboard and the chair...

---

### Post by Papa-san on 2006-11-29
> **Titus A Duxass said:**
> You are not scrooged (interesting usage), you have to do things manually.
What are you trying to install?

LOL...
I am trying to be polite... (I am in school to be a Pastor...)

---

### Post by Papa-san on 2006-11-29
It's really Quite amazing how silent my threads get once I post my hardware... LOL

---

### Post by PriceChild on 2006-11-29
> **Papa-san said:**
> It's really Quite amazing how silent my threads get once I post my hardware... LOLYou've been waiting not even half an hour... be patient please :)

---

### Post by KingBahamut on 2006-11-29
Broadcomm drivers. 

This is a bit of distaste I have. Have you attempted to use ndiswrapper (something Ive found more successful than trying to actually get the broadcomm drivers to run)? 

ATI drivers are an honest gruff. Difficult to deal with, however in Edgy I found it a bit easier to deal with.

---

### Post by Papa-san on 2006-11-29
> **PriceChild said:**
> You've been waiting not even half an hour... be patient please :)

;) Hence the LOL part!

I've been doing these forums for a while, and am OK with the wait... Anyways...

King Bahamut... 

Yes, I use the ndiswrapper exclusively. I have never had the 'native' driver work. 

Unfortunately, when I tried Edgy, nothing I did made my wireless work. The one that came with the 6.10, Ndiswrapper, removing and re installing and re-configuring ndiswrapper... Blacklisting the bcm43XX... Nothing... For whatever reason, it wouldn't find my card...

Within Dapper, I got it to find the card, but wouldn't associate with the access point. (Used to work OK with my old Linksys router, but we have since gone to DSL (from cable) They supplied their own modem/router. I had thought about hooking up the old router as well, but that just doesn't seem like a good idea... (Besides, this is not really a workable solution, as Dapper doesn't work with the video card. Edgy works with the video card drivers OK, though... What a pickle!

Breezy is a breeze!

What I need here is a way to install the java (jre-1_5_0_9-linux-i586.bin) that I have on my desktop. I figured that Automatix might be workable, as I have used it before... 
I found this: [http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)
but after looking through it, I am gauranteed to be doing a fresh install before I get halfway through it... 
This next link didn't (doesn't) work with my software version, or permissions, or knowledge or whatever... I guess:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) Can't seem to get the directories and folders to line up right. Either something isn't found where it's supposed to be, or I can't make it, etc., etc... Everything I do gets bashed...

---

### Post by Papa-san on 2006-11-30
Well, I broke down and upgraded to Dapper again. It took my four hours, but I got wireless working. Installed Automatix. So, that issue is resolved.

---

### Post by gertmul on 2006-12-11
Any chance you can post here how to get the BCM4306 Wireless Controller working, please? I have the same card, but "version: 03"

Thanks

---

### Post by taurus on 2006-12-11
> **gertmul said:**
> Any chance you can post here how to get the BCM4306 Wireless Controller working, please? I have the same card, but "version: 03"

Thanks
It's in his sig!!!

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by gertmul on 2006-12-11
Thank you for a quick resonse!

This worked for me:

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

