---
title: "Wireless: Realtek 8185, Gateway MT3423"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by clemrgooden on 2007-09-15
I am brand new to Ubuntu. I have a Realtek 8581 on a Gateway MT3423 laptop and would like to know the steps I need to take to setup and use wireless internet - 802.11 / WEP. Please help me! I have used Solaris before, so I'm not affraid of command-lines and the like. Thanks!

---

### Post by Maestro23 on 2007-09-15
> **clemrgooden said:**
> I am brand new to Ubuntu. I have a Realtek 8581 on a Gateway MT3423 laptop and would like to know the steps I need to take to setup and use wireless internet - 802.11 / WEP. Please help me! I have used Solaris before, so I'm not affraid of command-lines and the like. Thanks!

Welcome to the forums. You running Feisty?  This guide will get you going for your wireless.

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless)

---

### Post by confusedallthetime on 2007-09-16
I have same problem and the guiide you givelink to is ZERO help, unless your a died in the wool nerd programmer!!!!!!

---

### Post by bg1256 on 2007-10-16
I have the same laptop as the OP, and i would like to get it working as well...

---

### Post by Leonti on 2007-10-18
Hello!
I'm running Opensuse 10.3, but previously I was using Kubuntu 7.04 (but on another laptop).

I have MT3423 too, so I had the same problem.

**First solution** - if you are running 32-bit system you could try ndiswrapper drivers.
1. First you need to install ndiswrapper ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)).
It should be available with apt-get:
```
sudo apt-get install ndiswrapper-utils ndiswrapper-common
```
Or if you prefer, you can install it from source.
2. Than you need to download windows driver for use with ndiswrapper from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)

There is also driver for 64-bit version and theoretically it should work but I didn't manage it to.
3. After this you need to install this driver:
```
sudo ndiswrapper -i net8185.inf
```
To check whether driver installed or not run:
```
sudo ndiswrapper -l
``` - will list all installed drivers - if your card in this list it is installed.
4. Run ndiswrapper:
```
sudo modprobe ndiswrapper
```
With ```
dmesg
``` you can check on errors which this driver may produce.
If everything OK, your card should start working.

This did not worked for me because I have 64-bit system (theoretically it should with 64-bit ndiswrapper and 64-bit drivers). I did not dig into the problem because I managed native drivers to work :D But with 32-bit system everything should work smoothly. It worked for me for another card on another laptop.

[B]Second one.
[/B]Native drivers. As you can see on the Realtek download page you can find linux native drivers. Those drivers are no more than just old version of rtl-wifi project drivers: [http://rtl-wifi.sourceforge.net](http://rtl-wifi.sourceforge.net)
This is what worked for me.
They have very good installtion manual [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing) so I will not waste time writing the same thing you can read on official site.
Just add some things:
1. You need kernel-source package to be able to compile drivers:
```
 apt-get install kernel-source
```
2. If during 'make' process you will get errors - don't be afraid. All you need is to find right version of drivers for your kernel.
For example I have 2.6.22 kernel and newest drivers did not work for me. For this kernel works svn revision 58.
It might be similar for your kernel too - just try to find right one.

Good luck!

---

### Post by papabean on 2007-12-13
I have a Gateway MT-3422 (the model before the original poster's) and the only two drivers (that I've needed) that caused me any trouble in Linux were the onboard audio drivers and the Realtek 8185 wireless drivers.

I'm using ndiswrapper right now to use the wireless but would prefer a more native solution.  I've tried the drivers from source from Realtek's website - no dice.  The driver loaded but the wireless card could not attach to a network (with WPA).  The module in the kernel tree doesn't even recognize the hardware correctly. 

Thanks to this thread, I'm going to try the rtl-wifi sources and hope for the best.  I was able to follow Leonti's steps until here:
> 1. You need kernel-source package to be able to compile drivers:
```
 apt-get install kernel-source
```I wasn't able to install kernel-source.  The closest package I could find is linux-source.  I'll post again with results.
```
apt-get install linux-source
```

---

### Post by papabean on 2007-12-13
In the last hour, I've tried revisions 67, 62 and 58.  Revision 67 failed to compile (as stated in the rtl-wifi installation guide).  Revisions 62 and 58 fail to negotiate WPA via the Network Manager.

I've since reverted back to the ndiswrapper driver for now.  I will try again in the near future.

---

### Post by abeppu on 2007-12-13
I'm also trying to get my rtl8185 working -- but I'm a bit confused.  

Leonti, have you had any problems with the rtl-wifi drivers connecting to secure networks?  Mine connects fine to open networks, but causes kernel panic when I try to connect to WEP or WPA networks.  I've seen a few other posts to this effect, but I think they got around it with 32-bit ndiswrapper.  Did you do anything different in installing or compiling the rtl-wifi drivers that would make them different from the ones that are already included with ubuntu  (at least gutsy, according to the rtl-wifi FAQ).  If you have any suggestions, I'd appreciate them.

Papabean, do you have ndiswrapper working with the rtl8185 chipset on a 64 bit system, by any chance?  Or are you on a 32 bit system?  If you've managed the 64 bit ndiswrapper, presumably using win xp 64 drivers, could you elaborate on how you did it?  I've been struggling with it for a while.

---

### Post by Leonti on 2007-12-14
abeppu, actually I've worked only with open networks, so I don't know about those secure networks.
But, when I'm trying to connect to secure network with wrong password I have no problems / I just have a message that password is wrong, no kernel panic.
I hope it would help a little.

---

### Post by papabean on 2007-12-14
abeppu:  I am currently using 32-bit ndiswrapper.  I've had no success with 64-bit or the open drivers.  

leonti:  I get the same thing when I attempt to join my WPA-encrypted network.  It will attempt to connect as 128-bit WEP, so the authentication fails.  

No kernel panics in Ubuntu.  I experienced those in other distros, however, in regard to the wireless drivers.

---

