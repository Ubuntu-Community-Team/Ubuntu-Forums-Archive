---
title: "Wifi Problem"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Leigen_Zero on 2008-03-31
Hi there, I am not that experienced at linux, but finally quit windows and I am now running Ubuntu on my Sony VAIO PCG-K315b.

Basically I have been having trouble with my wireless PCMCIA card (A Buffalo WLI2-CB-G54l),  and after numerous guides have been able to get ndiswrapper to recognise the driver.  But would like some help on how to actually connect to wireless internet.

My router requires a password to connect to it if this info affects anything.

ndiswrapper -l reports:
neti2220 : driver installed
        device (17FE:2220) present

iwconfig wlan0 reports:
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

any help would be much appreciated

---

### Post by tompickles on 2008-03-31
Have you actually changed which module the wireless device actually needs? Not sure how to do this in Ubuntu/Debian based system - but I know I had to do that when i was on openSUSE.  You may also need to blacklist the old default module so that it doesn tload at boot. Try searching for that in relation to debian more generally than specificallly ubuntu.

---

### Post by m60dude5 on 2008-03-31
Have you tried playing with the settings for the wifi connection by clicking the computer icon in the top right hand corner?

---

