---
title: "wireless problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by kdt on 2006-04-15
hi

As you can see I'm a newb in linux. After briefly checking out some other distros (Mandriva and SuSE) I opted to install Ubuntu 5.10 on a dual boot. So far the majority of hardware is working but I've been having problems with getting my wireless to work. I've checked out a few websites and followed the ndiswrapper guide to setup the wireless with no joy :( 

my iwconfig brings up the following:

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Sparta"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:12:BF:0A:C3:74
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=77/100  Signal level=-27 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

my eth0 is working fine and by the looks of it the system recognises the card so why can I still not get the wireless to work?

Any help would be much appreciated.

Thanks

---

### Post by Bleachedbluejeans on 2006-04-15
Do you have a WEP key?
Is it entered correctly?
I'm a nOOb as well, but the links in my signature might help...

edit:
Oops, I'm logged in as my wife...

---

### Post by Papa-san on 2006-04-15
OK...links

---

### Post by kdt on 2006-04-15
thanks a lot for the reply mate

managed to get it working. Turns out I hadn't inactivated my wired connection Doh!- soon as I deactivated that and activated the wireless it worked great :D 

still havent got the wep key set yet, but hey at least I'm getting there

thanks again

---

