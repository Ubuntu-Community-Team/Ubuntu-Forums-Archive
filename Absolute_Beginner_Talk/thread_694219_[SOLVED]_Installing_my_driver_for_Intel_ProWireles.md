---
title: "[SOLVED] Installing my driver for Intel ProWireless 2200BG"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by jaigoose on 2008-02-11
I am completely new to linux and I happen to install it yesterday. I would like to install the driver for Intel ProWireless 2200BG. I was trying to follow the instructions in this forum but I encountered the following error

[I]jai@jai-laptop:~/Desktop/ipw2200-1.2.0$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-generic/include'.

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1[/I]

I am not much into computers but wanted to explore linux. It would be great if someone could guide me from this point. Here the result for iwconfig from my system
jai@jai-laptop:~/Desktop/ipw2200-1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by oedha on 2008-02-11
does it supposed to be ready to play ?
have you try ndiswrapper ?

---

### Post by LookTJ on 2008-02-11
This card should work out of box for Ubuntu. I have the same exact card.
```
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
```

---

### Post by PeterJS on 2008-02-11
> **jaigoose said:**
> 
jai@jai-laptop:~/Desktop/ipw2200-1.2.0$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This is proof positive that the driver itself is working, if it wasn't 1) the interface wouldn't have appeared, 2) it certainly wouldn't have the wireless extensions.

What are you trying to do, how, and what errors are you encountering?

---

### Post by Rocket2DMn on 2008-02-11
I use a 2915abg card which uses the ipw2200 driver - I did not have to install anything extra.  It looks like your card is already detected, so you just have to tell it to connect to a network.  Using nm-applet is probably the easiest way (it's in one of the panels).

---

### Post by jaigoose on 2008-02-11
I have not tried ndiswrapper. The thread I was following instructed me to download the driver and the firmware,which I have done and then I got stuck with that error midway. Can you please guide me through this ndiswrapper.

ndiswrapper - l does not list any installed drivers
jai@jai-laptop:~$ ndiswrapper -l
jai@jai-laptop:~$

---

### Post by jaigoose on 2008-02-11
I am trying to use my wireless internet which I use from windows. I tried to enter the credentials in wireless network settings but it did not work. I would like to activate my wireless card if it has been installed already

---

### Post by LookTJ on 2008-02-11
Do you have the network manager shown at the top right corner?(two computers icon) Click on it and select the network you want to connect to.

---

### Post by oedha on 2008-02-11
go to system - adinistration - network
did you see wireless icon ?
just like what others said...your card is ok....no need to install anything.......

---

### Post by jaigoose on 2008-02-11
Thank you very much, I guess it should really work out of the box. I probably had some issue with my wireless router as just a restart of the router helped me. Thanks for all your help

---

### Post by LookTJ on 2008-02-11
> **jaigoose said:**
> Thank you very much, I guess it should really work out of the box. I probably had some issue with my wireless router as just a restart of the router helped me. Thanks for all your help
You're welcome.

Go to thread tools and mark this thread as solved ;)

---

