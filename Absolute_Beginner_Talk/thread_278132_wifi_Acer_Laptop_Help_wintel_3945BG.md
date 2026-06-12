---
title: "wifi Acer Laptop Help w/intel 3945BG"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by redDEADresolve on 2006-10-15
I just bought an Acer Aspire 3600 laptop, everything is working great acept the wireless card. I have an intel 3945BG wireless card, the light is on, it work in windows.

I've tried a bunch of guides and how-to's but nothing works

Help me Ubuntu geeks you're my only hope

---

### Post by shoujulei on 2006-10-15
Greetings.  What is your current configuration?  Are you using Dapper Drake, Edgy Eft, i386, x86_64, i686?  What you need is for ubuntu/kubuntu/xubuntu to install the ipw3945d into the proper folder.  This seems to be happening in your situation, as the wireless card is recognized.  Have you tried to type the following in the terminal: ```
sudo dhclient wlan0
```(or eth1) depending on what your computer calls your wireless card?  If you could try this and report back on what you see, then that would help alot in solving your problem.  If you're not sure what the computer calls your wireless card, then try typing the following in the terminal: ```
sudo iwconfig
```.

---

### Post by redDEADresolve on 2006-10-15
I'm running Dapper Drake standard kernel for ubuntu 2.6.15-27-386
this is what i got when i ran your command line prompts

red@red-laptop:~$ sudo dhclient wlan0
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
red@red-laptop:~$


red@red-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

red@red-laptop:~$

---

### Post by capn_hector on 2006-10-15
try an iwlist scan and see what it does.  also make sure there is a driver that supports your card with your install.

---

### Post by redDEADresolve on 2006-10-15
> **capn_hector said:**
> try an iwlist scan and see what it does.  also make sure there is a driver that supports your card with your install.

red@red-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by capn_hector on 2006-10-15
> **redDEADresolve said:**
> red@red-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

its got to be a driver issue.  try using this howto to install the driver

[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

---

### Post by shoujulei on 2006-10-16
I had the same problem when I moved from the 2.6.15-26 to the -27 kernel; what I did was the following (in terminal)```
sudo cp /sbin/ipw3945d-2.6.15-26-386 /sbin/ipw3945d-$(uname -r)
``` this was while I was booted into the -27 kernel; upon reboot and sudo dhclient eth1 (also in terminal) I was good to go.  Another consideration (if the above doesn't work) is what sort of encryption are you using? WEP? WPA?  I use simple MAC address filtering on my wireless base station as I am too lazy to get WEP/WPA working.  You may want to turn off encryption while seeing if you can get the base station to accept your dhcp request (dhclient etc.); if it does w/o encryption then you know it's a WEP/WPA issue.  Try first without, then report back on what your results are.  Hope this helps you sort it out.

---

### Post by redDEADresolve on 2006-10-16
> **shoujulei said:**
> I had the same problem when I moved from the 2.6.15-26 to the -27 kernel; what I did was the following (in terminal)```
sudo cp /sbin/ipw3945d-2.6.15-26-386 /sbin/ipw3945d-$(uname -r)
``` this was while I was booted into the -27 kernel; upon reboot and sudo dhclient eth1 (also in terminal) I was good to go.  Another consideration (if the above doesn't work) is what sort of encryption are you using? WEP? WPA?  I use simple MAC address filtering on my wireless base station as I am too lazy to get WEP/WPA working.  You may want to turn off encryption while seeing if you can get the base station to accept your dhcp request (dhclient etc.); if it does w/o encryption then you know it's a WEP/WPA issue.  Try first without, then report back on what your results are.  Hope this helps you sort it out.

red@red-laptop:~$ sudo cp /sbin/ipw3945d-2.6.15-26-386 /sbin/ipw3945d-$(uname -r)
Password:
cp: cannot stat `/sbin/ipw3945d-2.6.15-26-386': No such file or directory
red@red-laptop:~$

I think I have to install that driver but the directions are pretty tuff. anyone know of a deb file that would do it?

---

### Post by fragos on 2006-10-16
I installed Ubuntu on a dfferent version of Acer Aspire laptop.  It has a Broadcom chip set.  I installed ndiswrapper and then the recommended driver.  I ran into some trouble with gnome-network-manager and ultimately uninstalled it totally.  I found wifi-radar a better choice.  The network monitor applet was also useful and when using wifi an extra applet bar icon pops up to show signal strength.  On this Acer the wireless chip set was identified as eth1.

---

