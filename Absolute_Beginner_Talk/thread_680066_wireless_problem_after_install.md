---
title: "wireless problem after install"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by matthateswindows on 2008-01-27
I just installed Xubuntu 7.10 after using the live cd for a few days. When I was on the live cd, my wireless network was detected automatically, no problem. Even my neighbor's network was showing. Now that I installed, I seem to have no wireless and definitely no auto detection. Here's my iwconfig:

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Right now I am trying to use a 2wire card and router from at&t, but I also have a USRobotics card and a gigafast USB adapter I have tried with no luck, and I have the Windows cd that came with the cards.
Any help would be greatly appreciated.

---

### Post by amazingtaters on 2008-01-27
do you know what wireless drivers you have installed? The 2Wire cards use the orinoco drivers ([[color=blue]link[/color]](http://www.nongnu.org/orinoco/)) so try getting those installed and see if your wireless card starts working then.

---

