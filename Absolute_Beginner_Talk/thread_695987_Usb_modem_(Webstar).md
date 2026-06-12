---
title: "Usb modem (Webstar)"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Healer on 2008-02-13
I want to know how to connect to internet using, the usb cable to my webstar modem, I have a dell CpxH (PPX), I don't have those cards you put in the laptop, and I have a USB 1.1, I connected it, and linux shows that it connect, the network thing on the top right corner showed it was connected, but when I turned on the internet and went to a website, I didn't work. Help por favor plz!!

---

### Post by Jewfro_Macabbi on 2008-02-13
how did you configure your connection?

You can do it via sytem - network

you can do it via wvdial - edit /etc/wvdial.conf - then execute sudo wvdial to connect

or you can do it using pppconfig

sudo aptitude install pppconfig

then sudo pppconfig

---

### Post by dstew on 2008-02-13
That is a cable modem, correct? That is, it is connected to cable, not to the phone lines, right? Open a command line (Applications --> Accessories --> Terminal) and enter```
lsusb
```Post the results to the forum. Also post the result of the command```
ifconfig
```

---

### Post by Healer on 2008-02-13
well I plugged it in and it showed the icon change show it's connection, yes it connects to the cable, I'm new to this so bare with me and I will try your ideas and will post the results

---

### Post by Jewfro_Macabbi on 2008-02-13
If Ubuntu detects the modem then you just need to configure it to connect to your ISP using one of the above methods.

---

### Post by Healer on 2008-02-19
okay so I'm trying your methods right? and I'm trying th network via system. Well it shows the form i will be connecting to (when disconnected it doesnt show). I go to the properties of it and it shows: 
the IP address box
the Subnet Mask box
and the Gateway Address box
How do I fill these out so they work?

---

### Post by Jewfro_Macabbi on 2008-02-19
If this is to connect to your internet then mostly likely you need to change it to DHCP, not static, and it will assign the values for you when you connect.

---

### Post by djole_nisam_ja on 2008-04-07
For dstew, as promissed, but for everyone else also.

I use Ubuntu 5.10 on this laptop: [http://www.berndnoetscher.de/notebook.html](http://www.berndnoetscher.de/notebook.html)

and I have the same modem that I need (as you can see by PC specification above) to connect via USB.

The response to command **lsusb** is:

**Bus 001 Device 001: ID 0000:0000**

and the response to command **ifconfig** is:

lo            Link encap:Local Loopback
_______inet addr: 127.0.0.1 Mask: 255.0.0.0
_______inet6 addr:  ::1/128  Scope:Host
_______UP    LOOPBACK    RUNING    MTU:16436      Metric:1
_______RX packets:2053    errors:0     dropped:0    overruns:0    frame:0
_______TX packets:2053    errors:0     dropped:0    overruns:0   carrier:0
_______collisions:0   txqueuelen:0
_______RX bytes:178710 (174.5 KiB)     TX bytes:178710(174.5 KiB)

---

### Post by dstew on 2008-04-07
The device is not being detected by your USB. Are you sure it works? Does your laptop only have 64 MB memory, as the document says?

---

### Post by djole_nisam_ja on 2008-04-07
Yes it has only 64 MB of RAM and device works ok cause I use it on this machine I you to write you.

What to do?

Maybe some USB driver is missing?

P.S. When I installed Ubuntu 5.10 for the first time, it saw my USB connected modem but now it doesn't. I tried reinstalling and it's the same,

**BUT** first time package **CONFIGURE NETWORK CARD** was installed and system saw the modem through this package but now this package wasn't installed. When I try to install it system says that some **UNIVERSE** repo should be enabled and system try to download this package from internet.

What to do?

---

### Post by dstew on 2008-04-07
> When I try to install it system says that some UNIVERSE repoTo enable the Universe repository, open the synaptic package manager, click on the Settings tab --> Repositories, check the Universe repository.

Are you running Ubuntu 7.1 on the machine with 64 MB memory? I did not think that was possible.

---

### Post by djole_nisam_ja on 2008-04-08
> **dstew said:**
> To enable the Universe repository, open the synaptic package manager, click on the Settings tab --> Repositories, check the Universe repository.

Are you running Ubuntu 7.1 on the machine with 64 MB memory? I did not think that was possible.

I know how to enable UNIVERSE repo, BUT system requires to download CONFIGURE NETWORK CARD package from internet while I'm trying to enable net connection.

It's stupidity.

I don't run Ubuntu 7.10 on this machine BUT Ubuntu 5.10.

---

