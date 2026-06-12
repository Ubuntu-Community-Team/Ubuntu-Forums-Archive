---
title: "Speedtouch 330  on Ubuntu Gutsy"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by carnageblood on 2007-10-14
Hy everybody ! This is my first post on this site  so a I need some welcoming! I have some problems with my Speedtouch 330 I can not install it properly in Ubuntu Gutsy 7.10   thou' it worked with absolutely no problems in Kubuntu 7.10 or in Ubuntu 7.04 . The method i used it's the one with a bootscript in init.d called dial!
In my sys.log I can see the message "Adsl line is up" and indicating the usual speed. What seems different is that I can see "pap authentification succesfully" or somthing like this. Anyway I need that someone points me to a tutorial or program that can make speedtouch work well in Gutsy. 
 Please help me cause I can wait no more the delete everything on my HD related to M$! Thank's in advance!

---

### Post by milosz.galazka on 2007-10-14
Tutorial like [this]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html")?

---

### Post by carnageblood on 2007-10-15
I've allready tried that one and does not work on a freshly  installed Gutsy! Is there one working on 7.10 or not?

---

### Post by milosz.galazka on 2007-10-15
What about [this]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page")?

---

### Post by carnageblood on 2007-10-15
I'll try it right away!

---

### Post by carnageblood on 2007-10-15
Confirmed not working on gutsy! I don't know what else to do!

---

### Post by snake444 on 2007-10-15
you said it works on kubuntu 7.10 so install there the package ubuntu-desktop and login with gnome
maybe it will solve the problem:lolflag:

---

### Post by jgrabham on 2007-10-15
[https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

Does that work?

---

### Post by carnageblood on 2007-10-15
> **jgrabham said:**
> [https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

Does that work?

It's not officially supported by Gutsy and it does not seem to wok!
What it's strange is the fact that in var/log/sys.log it outputs "ADSL line is up" but there's no f***n connection!Damn' it it's driven me crazy!

---

### Post by carnageblood on 2007-10-15
> **snake444 said:**
> you said it works on kubuntu 7.10 so install there the package ubuntu-desktop and login with gnome
maybe it will solve the problem:lolflag:

I'd bet it works but hey I want Ubuntu not Kubuntu and there seems to be some difference between them!

---

### Post by kostkon on 2007-10-15
I would like to ask you to be more specific. I mean, several people gave you some suggestions and the only thing you say is that it does not work.

It would be much better if you could provide some additional information in order to be able to help you. Furthermore, you will help many people that use this modem, and would like to know whether it is actually working in *Gutsy* (before they do the upgrade and lose their connection to the internet).

Could you describe of what is happening with the modem, where is the wrong with it? Could you tell what is working and what not? Do the lights blink as they supposed to?

Also, could you paste here the output of your *demsg*
```
dmesg | tail
```

or the part of it that is specific to the connection.

Also, please paste the output of the *ifconfig* command
```
ifconfig
```

---

### Post by carnageblood on 2007-10-16
Yeap the light are blinking so the firmware is loaded just fine!

---

### Post by carnageblood on 2007-10-16
I did a clean install of Ubuntu 7.10 and I started with this [tutoriall]("http://linux-usb.sourceforge.net/SpeedTouch/ubuntu/index.html") but  I have no connection!I did exactly how it says there!
The output for ```
dmesg | tail
``` is this:
```
[   46.426698] Bluetooth: L2CAP ver 2.8
[   46.426703] Bluetooth: L2CAP socket layer initialized
[   46.514647] Bluetooth: RFCOMM socket layer initialized
[   46.514921] Bluetooth: RFCOMM TTY layer initialized
[   46.514927] Bluetooth: RFCOMM ver 1.8
[   58.078255] ATM dev 0: ADSL line is up (2048 kb/s down | 384 kb/s up)
[  204.790156] eth0: link down
[  208.006987] NET: Registered protocol family 10
[  208.007197] lo: Disabled Privacy Extensions
[  208.007332] ADDRCONF(NETDEV_UP): eth0: link is not ready
```
and for
```
ifconfig
```
the output is this:
```


eth0      Link encap:Ethernet  HWaddr 00:13:8F:42:0B:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9488 (9.2 KB)  TX bytes:9488 (9.2 KB)

```
I have also atached a copy of sys.log. I've put it in ".xcf" so I could upload it. Open it with any text editor!
Plese tell me were I did wrong!

---

### Post by giornata on 2007-10-17
I was very disappointed to find that the Speedtouch 330 didn't work on Gutsy. I was even more disappointed to find that 'usbadslmodemmanager' didn't work either (although I expect that will soon be fixed), nor did the various hand-cranking methods described.

However, 'ubudsl' ( [http://ubudsl.ubuntu.pl/index_en.html]("http://ubudsl.ubuntu.pl/index_en.html") ) does work, although I should point out that this was not immediately after a clean install, but after I had tried the hand-cranking methods.

These problems with Speedtouch 330 and Ubuntu have been around for some time, and it is disappointing that they have still not been addressed.

Mandriva 2008 One detects the Speedtouch on install, and it just works.

---

### Post by carnageblood on 2007-10-17
I tried ubudsl but my country or my isp aren't listed there. If you can please send me an e-mail with what's necessary to make speedtouch work in ubuntu!

---

### Post by giornata on 2007-10-17
> **carnageblood said:**
> I tried ubudsl but my country or my isp aren't listed there. If you can please send me an e-mail with what's necessary to make speedtouch work in ubuntu!

I can't tell you how to make Speedtouch work in Ubuntu other than what I said in my previous post. If your country and isp aren't listed in ubudsl, your best bet is to contact the developers of ubudsl via their web site.

---

### Post by giornata on 2007-10-19
Well, things aren't what they seemed! In my first post I said:

"However, 'ubudsl' ( [http://ubudsl.ubuntu.pl/index_en.html](http://ubudsl.ubuntu.pl/index_en.html) ) does work, although I should point out that this was not immediately after a clean install, but after I had tried the hand-cranking methods."

I've just done an install of the final ubuntu 7.10 (the previous was the release candidate). I then ran ubudsl and --- no internet connection. 

So:
[LIST=1]
[*]I uninstalled ubudsl;
[*]ran through the hand-cranking for PPP over ATM as described in  "https://help.ubuntu.com/community/UsbAdslModem/Speedtouch";
[*]installed and ran ubudsl.
[/LIST]
This did the trick, and I have a working internet connection.

---

### Post by philheaton on 2007-10-19
i was having the same problem. there is a simple solution to this but it won't work on a clean install of gutsy. 

after much gnashing of teeth and tearing of hair, i did a clean install of feisty, installed usb adsl modem manager to get an active connection, then simply upgraded to gutsy through update manager.

internet connection working fine

hope that helps

---

### Post by TimGS on 2007-10-20
I am also having problems. I have a clean install of 7.10, and am new to Linux. I'm computer literate but am linux illiterate (last used Unix about 13 yrs ago).

Tried Steve Harper's package - an icon appears at the top of the screen with 'Connect', 'Disconnect', etc options when you right click on it. When you hover over it, you get the message 'Starting Up'. I've now uninstalled this.

Fell down at the first hurdle with the manual methods - I have directory /proc/bus/usb but within this there is no devices directory - or anything at all for that matter (both manual methods ask you to type in a command that refers to /proc/bus/usb/devices. I did optimistically skip the firmware section as a result and continued with the instructions under 'Secrets' and 'PPP over ATM' but obviously was doomed to failiure! (I used the page at [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)).

Under the System option on the Admin menu 7.10 recognises a Speedtouch device on USB but doesn't claim to know anything else about it.

If I succeed in updating the firmware on the modem will it affect my connection from XP (I have a dual boot set up)?

Am about to try ubuDSL, although looking at this forum I will still need to hand crank, which sadly I'm stuck on.

-- Tim.:confused:

---

### Post by StevenHarper on 2007-10-21
Hi,  I just fixed and uploaded a Version of the USB ADSL Modem Manager

it is tested and works in GUTSY 7.10 32bit

Please get it here

[http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/](http://www.squeezedonkey.com/svn/linux/trunk/releases/ubuntu/32-bit%20i386/)

Thanks

Steve

---

### Post by FreewheelinFrank on 2007-10-21
Many thanks!

In the case of an upgrade, is it necessary to uninstall the old version, or can the new version be installed over the old?

---

### Post by StevenHarper on 2007-10-21
No you can just put the new one over the top, it will be fine

Steve

p.s Please put feedback in this MAIN thread

[http://ubuntuforums.org/showthread.php?p=3594280#post3594280](http://ubuntuforums.org/showthread.php?p=3594280#post3594280)

ta

---

