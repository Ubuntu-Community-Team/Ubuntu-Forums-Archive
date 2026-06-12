---
title: "airport card not detected?"
date: 2013-02-01
forum: Apple Hardware Users
---

### Post by E411 on 2013-02-01
Hi there, I'm running lubuntu 12.10 on a PowerBook G4 and I can't even figure out what my wireless card is.

sudo lshw -C network

```
*-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:30:65:16:bf:26
       capabilities: ethernet physical wireless
       configuration: boroadcast=yes driver=airport driverversion=3.5.0-17-powerpc-smp firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```

lsmod  | grep airport

```
airport           3658           0
orinoco       70654           1 airport
```

iwconfig

```

lo no wireless extensions.

eth1 IEEE 802.11b ESSID:""
Mode:Managed Frequency:2.422 GHz Access Point: None
Bit Rate:11 Mb/s Sensitivity:1/0
Retry limit:8 RTS thr=2347 B Fragment thr:off
Power Management:off
Link Quality=0/70 Signal level=-122 dBm Noise level=-122 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

---

### Post by iMac71 on 2013-02-02
try the following command:```
lspci | grep Network
```it should show something like this:```
04:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
```

---

### Post by E411 on 2013-02-02
Hello iMac71,

Oops, I forgot to mention that 

```
lspci | grep Network
```

outputs... nothing.

lspci without piping gives USB controllers, Firewire and Ethernet controller

---

### Post by iMac71 on 2013-02-02
Do you have an OS X CD, from which you may run System Profiler? It seems that this be the unique way you have for finding infos about your wireless card, since Ubuntu 12.10 doesn't give any info about it.

---

### Post by E411 on 2013-02-02
> **iMac71 said:**
> Do you have an OS X CD, from which you may run System Profiler? 

I don't :lolflag:

---

### Post by iMac71 on 2013-02-03
are you sure you have an airport card on your powerbook? [These technical specifications]("http://support.apple.com/kb/SP114") indicate that your powerbook is airport ready, but that it doesn't have pre-installed that card.

---

### Post by E411 on 2013-02-03
Yes, I'm sure it does, I used to run OS X on that puter. Although the airport card was kinda going up and down, which I thought was due to the system. The network management tool was constantly telling me that an application had changed my configuration.

---

### Post by iMac71 on 2013-02-03
Do you have at least the live CD of your Ubuntu release? If yes, boot a live session, and then verify if there are additional drivers related to wireless connection.

---

### Post by E411 on 2013-02-05
> **iMac71 said:**
> Do you have at least the live CD of your Ubuntu release? If yes, boot a live session, and then verify if there are additional drivers related to wireless connection.

I don't have the live cd either, I installed the iso from the hard drive as the system wouldn't boot on the usb stick. Should I try installing various drivers and see what happens?

---

### Post by iMac71 on 2013-02-05
since in your first post it's mentioned the word "orinoco" related to your airport device, perhaps you might find some help at the following link:
[http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco)

---

### Post by este.el.paz on 2013-02-05
@E411:

Based upon my recent experience with Lu 12.04 LiveDVD in my iBook G4, the network applet drop down showed "device not ready" for the wireless, and it probably relates to one of the "b43" drivers, either "legacy" or regular that needs to be installed.  I went to the Ubun PPCFAQ page and it lists some info there; I recall doing this for each of my PPC computers several times, pretty easy on the Terminal, you just have to check which Broadcom card you have to know which driver you need.

[https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

e.e.p.

---

### Post by rsavage on 2013-02-05
It is an airport classic card, not an airport extreme (which are the broadcom ones).

If you can't see your networks then make sure you haven't set them to be hidden!

Also sometimes you have to toggle the 'Enable Wireless' and  'Enable Network' settings.  Even if they are ticked it is worth turning them off and on again.

---

### Post by este.el.paz on 2013-02-05
> **rsavage said:**
> It is an airport classic card, not an airport extreme (which are the broadcom ones).
If you can't see your networks then make sure you haven't set them to be hidden!
Also sometimes you have to toggle the 'Enable Wireless' and  'Enable Network' settings.  Even if they are ticked it is worth turning them off and on again.

@rsavage:  OK, cool . . . I saw "broadcom" in one of the posts, and by the time I posted I wasn't recalling that it was "iMac" that put that there as an example . . . hopefully my link to the PPCFAQ would provide the correct options to help solve the problem in spite of my "Broadcom" gaffe . . . .  I was just trying to speed the plow, based upon the fair number of Linux installations I've done just trying to get something to run on my PPC iMac & iBook and the numerous discussions on the mintppc forum as well, with many posters inquiring about wireless issues, and each time wifi needed some driver to be added . . . and then the problem was more or less fixed.  Even with the fairly high zoot LM Maya system on my MBPro wifi did not work "out of the box" and needed the "b43???" driver to be "apt-get'd" and "install" and so forth.  Is this only an issue with Apple computers trying to run Linux-based systems??  I don't know, but it seems fairly prevalent IMHE . . . .  Even in testing the Lu 1204 LiveDVD on the iBook (the more recent version) . . . as I mentioned in my previous post, wifi showed "device not ready" . . . would the installer fix that problem during the install?? possibly, don't have time to go through that yet . . . .  Hopefully the OP will find the data he needs on the PPCFAQ and get his wifi issues straightened out . . . .  It sure would be nice if it only took toggling the "Enable wireless" button . . . so far that hasn't been an option for fixing the wifi connection problems I've run into . . . it takes the right driver . . . .  : - )))

e.e.p.

---

### Post by E411 on 2013-02-09
> **rsavage said:**
> 

Also sometimes you have to toggle the 'Enable Wireless' and  'Enable Network' settings.  Even if they are ticked it is worth turning them off and on again.

Just noticed I can't untick 'Enable Wireless' nor 'Enable Network' as clicking would just close the drop down menu. Same thing with Edit or Information. I can connect/disconnect my wired network through the same menu though.

---

