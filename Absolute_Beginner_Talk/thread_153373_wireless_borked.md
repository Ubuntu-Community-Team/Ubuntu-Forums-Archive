---
title: "wireless borked"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by wile_e8 on 2006-03-31
OK, I've had some weird problems with my wireless, and I've searched through these forums for all the possible fixes, and none of the wireless fixes seem to work.  I had my wireless set up using ipw2200 + wpasupplicant as described in [thread=26623]this thread[/thread].  It was working just fine.  However, my wireless card stopped working.  I apparently hit a button on my laptop that turns the wireless signal on and off.  I didn't notice this until I booted up in windows trying to fix the problem, and hitting this button turned it on (it is lit up when wireless is on).  However, I have been unable to get wireless working in Ubuntu since.  I have retried the steps in the above thread several times, and it never works.  I have searched these forums for any possible solution, and none of them work.  Is it possible that there is a setting that was turned off when I hit this button that I need to turn on?  This is frustrating, I've had Ubuntu about a month and a half and it was working fine for the first month, but no matter what I try I can't get it back to the way it was.  Somebody please help me.

---

### Post by trent dillman on 2006-03-31
```
iwconfig
```

Whichever interface has wireless, do this (assuming wlan0):

```

sudo ifdown wlan0
sudo ifup wlan0

```

---

### Post by wile_e8 on 2006-04-01
FWIW here's what I got, I didn't have the wired ethernet (eth0) plugged in when I tried this if it matters.  Still not working.

```
allan@wileylap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

eth1      IEEE 802.11g  ESSID:"allan"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:6D:50:B6
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

allan@wileylap:~$ sudo ifdown eth1
Password:
ifdown: interface eth1 not configured
allan@wileylap:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:d5:a0:7d
Sending on   LPF/eth1/00:12:f0:d5:a0:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Looking at the iwconfig output reminds me, I currently have the newest versions of the of drivers/firmware for the ipw2200 install from the howto thread, not the versions named in that thread.  The version in the howto were what originally worked for me.  I don't know if it matters, it's just the last stuff I tried after the other stuff didn't work either.  I don't know if the warning for the versions is related to.

---

### Post by wile_e8 on 2006-04-01
And while I'm at it, here's the ipw2200 messages from dmesg, it has an error that I couldn't find a solution to in the forums, although I did see other people with this error.

```

allan@wileylap:~$ dmesg | grep ipw
[4294698.387000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.0
[4294698.387000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294698.391000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294699.342000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[4294701.977000] ipw2200: Can't set TKIP countermeasures: crypt not set!

```

I'm just putting this out there too in case it matters, maybe someone will see something and know the solution.

---

### Post by trent dillman on 2006-04-01
iwconfig --version

That error you're getting might be a problem...

---

### Post by wile_e8 on 2006-04-01
```

allan@wileylap:~$ iwconfig --version
iwconfig  Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v18.

Kernel    Currently compiled with Wireless Extension v17.

eth1      Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v17.

```

OK, what is the wireless extension?  Is that one of the drivers (which actual versions do I need to download to get v18?)  Or what else is it?

---

### Post by wile_e8 on 2006-04-01
I don't know if there are any rules against bumping threads, but now my question is on the fifth page and I don't know if it's going to get noticed.  I was getting lead down the trail to getting help I do believe, but I need an answer to the last question, I can't find it in the forums.  How would I update the wireless extension to v18?

---

### Post by morphis on 2006-05-04
Hey 
The wireless extension make part of ur kernel...
u have to pgrade it or to apply a patch...for more info see
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html)
maybe it can help u:D

---

