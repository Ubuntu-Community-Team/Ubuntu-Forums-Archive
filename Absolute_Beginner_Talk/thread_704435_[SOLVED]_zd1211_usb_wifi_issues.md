---
title: "[SOLVED] zd1211 usb wifi issues"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by lil0tik on 2008-02-22
Hey all -

I recently bought a generic zd1211-based USB dongle for use with my Dell 1501 laptop (running Gutsy).

Essentially, I bought the dongle because it was pretty much my only option for attaching an external antenna to the computer (which has no PCMCIA slot).  Problem is, while Ubuntu seems to recognize the device, it refuses to connect to available APs.

Output from iwconfig is:
> 
eth2      IEEE 802.11b/g  ESSID: off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It's also recognized by lsusb:> 
Bus 006 Device 003: ID 0ace:1215 ZyDAS 


Any help getting this this working would be appreciated.  I'm still a Linux noob, but am comfortable working from the command line & will gladly provide any additional info.

---

### Post by Hightide on 2008-02-24
Hi

As you have a Zydas chipset, have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=49070")

regards

:)

---

### Post by lil0tik on 2008-02-24
Thanks, I'll check it out.  I'm usually pretty good at doing my research before posting questions.  I saw a few other threads about installing the zd1211rw driver (the driver used w/ my device) on older versions of Ubuntu, and similar issues, I still haven't found anything that quite matches my prob.  

The device seems, by all accounts, to be working. It can detect APs, it shows up as what it is when looked for w/ lsusb and iwconfig... but when it tries to connect to an AP, it takes forever & never finishes the connection (seems not to be able to get an IP from the host)...

---

