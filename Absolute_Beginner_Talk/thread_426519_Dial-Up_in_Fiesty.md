---
title: "Dial-Up in Fiesty"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Midgetmunky13 on 2007-04-28
im trying to get on the internet with my SoftV92 Data Fax Modem. i no that not all modems work but wen i had dapper i tried to do the one program that detects your modem or whatever but i didnt really know what to do. i need help with this.

---

### Post by solar george on 2007-04-29
If it is an internal modem do,

```
lspci
```

If it is on usb do 
```
lsusb
```

And post the results.

---

### Post by Midgetmunky13 on 2007-04-30
so where do i put that code? just in the terminal or in a special place or what?

---

### Post by oilchangeguy on 2007-04-30
terminal

---

### Post by Midgetmunky13 on 2007-04-30
alright thanks man

---

### Post by Midgetmunky13 on 2007-04-30
heres the text it gave me:


marcus@marcus-desktop:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 03) 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] 
00:03.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) 
00:04.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09) 
00:05.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01) 
00:06.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10) 
00:14.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22) 
00:14.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) 
00:14.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) 
00:14.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) 
00:14.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30) 
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by oilchangeguy on 2007-04-30
see item 5, your modem is listed. but probably not properly configured. go to system, admin, networking (don't use 7.04 not sure if networking is listed) open networking, what's listed?

---

### Post by Michl on 2007-05-01
System->admin->networking is useless for dialup
in edgy and feisty.

Search the forums for wvdial and gnome-ppp.  Also
see HowtoDialup in documentation in ubuntu.com

M

---

### Post by oilchangeguy on 2007-05-01
read this:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Midgetmunky13 on 2007-05-01
ok i downloaded the scanModem.gz on to my flashdrive. i tried to do what it is telling me but i can get anywhere with it. can somone give me a better step by step please?

---

### Post by Matchless on 2007-05-02
You require drivers to be installed for your Conexant HSF modem. Unfortunately the old Conexant open source drivers do not work on the latest kernels used in Edgy or Feisty. I suggest that you go to the Linuxant [http://www.linuxant.com/drivers/hsf/downloads-license.php?PHPSESSID=b299de244c70ea8a9323ccbd65d59047site](http://www.linuxant.com/drivers/hsf/downloads-license.php?PHPSESSID=b299de244c70ea8a9323ccbd65d59047site) as they are the only source of drivers that will work on your specific modem. You can download the modem driver for free, but it is then throttled to 14400 speed and they require you to register and pay a fee to get a registration code to open up the modem to 56k.
I suggest you try the free modem and get your PC working, albeit at a slow speed, and then decide if you want to pay the registration cost.
Hope this helps

---

### Post by fruitsofherwomb on 2007-05-02
wait is gnome-ppp built in Ubuntu, if it isn't the thing does the code 'sudo apt-get install gnome-ppp' wouldn't that mean I have to be ONLINE to do that code? Sounds kinda dumb making the guide require internet connection when the guide is to get a modem working.

---

### Post by GrueTamer on 2007-05-02
> **Midgetmunky13 said:**
> ok i downloaded the scanModem.gz on to my flashdrive. i tried to do what it is telling me but i can get anywhere with it. can somone give me a better step by step please?You want to configure and install it, extract the gzipped file and look for a readme on it.  If there's no readme, you may be able to do something like this.

```
cd <directory of extracted file> && ./configure
```

I'm not sure if you need root privileges or not to configure it, but if you do, just put sudo in front of ./configure.

Then, to install it, you may have to do something like...

```
make
```

Then, 

```
make install
```

You might need to be root to do that, but I'm not sure.
But check for a readme or install instructions, there are probably better instructions in there.

---

### Post by Bartender on 2007-05-03
> **fruitsofherwomb said:**
> wait is gnome-ppp built in Ubuntu, if it isn't the thing does the code 'sudo apt-get install gnome-ppp' wouldn't that mean I have to be ONLINE to do that code? Sounds kinda dumb making the guide require internet connection when the guide is to get a modem working.

Catch-22

You have to lug your PC to school or work or the library or a friend's house, plug into their broadband, then turn your PC on.  Linux is a joy with broadband, drudgery on dial-up

---

### Post by jis on 2007-05-16
:oops:

---

