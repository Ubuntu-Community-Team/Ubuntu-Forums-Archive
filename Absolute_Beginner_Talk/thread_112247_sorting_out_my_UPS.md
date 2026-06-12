---
title: "sorting out my UPS"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Aviatrixie on 2006-01-03
Hi all,

   I'm now 2 weeks in my Linux journey and have everything pretty much up and running. The one thing I hadn't gotten around to was putting the "smart" back into my APC Back-UPS ES series battery-backup unit, so that's been my project tonight. After much googling I finally figured out that I needed apcupsd and installed that, apcupsd-cgi, and the docs with synaptic. Synaptic reported a successful install, but I can't find anything to indicate that it actually has been installed anywhere except the green boxes in synaptic. I checked system monitor and can't find any daemon running that looks like it could be apcupsd. I also downloaded the dev's pdf on how to do this but must admit it was a bit over my newbie head.

   I am using a single computer with a single UPS, and am using the usb cable that came with my UPS, so according to the pdf it should be a simple set-up. Typing cat /proc/bus/usb/devices in shell gives me this (amongst a bunch of other stuff):

S:  Manufacturer=APC
S:  Product=Back-UPS ES 350 FW:800.e5.D USB FW:e5
S:  SerialNumber=AB0426128730
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid

   So... I guess the daemon is installed and Breezy can see my UPS fine. But when I try to start apcupsb manually from bash I get this:

erika@ubuntu:~$ /etc/rc.d/init.d/apcupsd start
bash: /etc/rc.d/init.d/apcupsd: No such file or directory

Anyway, I'm really trying to sort this out, but I think I need to hear the voice of experience about now. 

What is this newbie missing?

Thanks,

Erika

---

### Post by mlambie on 2006-05-02
[QUOTE=Aviatrixie]Hi all,
erika@ubuntu:~$ /etc/rc.d/init.d/apcupsd start
bash: /etc/rc.d/init.d/apcupsd: No such file or directory
[/QUOTE]

I'd expect it's just /etc/init.d/apcupsd (no rc.d). I hope this works.

---

### Post by jeremy on 2006-05-03
Have you edited your /etc/apcupsd/apcupsd.conf file?
More info about that at [http://www.apcupsd.org/manual/After_Installation.html#SECTION000121000000000000000](http://www.apcupsd.org/manual/After_Installation.html#SECTION000121000000000000000)

---

