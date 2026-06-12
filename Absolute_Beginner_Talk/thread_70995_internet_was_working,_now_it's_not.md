---
title: "internet was working, now it's not"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-10-02
i have a external modem (serial), i think its a rockwell 56k. Anyway i tried ubuntu warty a while back and had similar problems, but i did get the internet working fine useing wvdial with that install. Now this a new computer and i have hoary cd's which came in the post, so i thought double boot with win xp on my 3 gig pentium 4, all seemed fine, before on warty i had heaps of problems , i could connect to the internet with ppp but it was hopelessly slow,but withwvdial it worked as good as windows.
Now at first with hoary i tried just going to network and typing in user name dial up number and password and it detected my modem on devttyo. clicked on activate and it dialed up perfectly fast as dial up goes, ll happy. so i started updating programs i typed at a terminal apt-get update and away it went, since it takes many hours to update i left it running overnight, when i came in ,in the morning it said some updates could not be retireved. now when i dial up my internet connection has become incredibly slow like it was in warty, i have tried wipeing it off and starting again but still slow.
so i tried wvdial and it says no modem detected.
anyone help with this mess?

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=porsher_puddles]i have a external modem (serial), i think its a rockwell 56k. Anyway i tried ubuntu warty a while back and had similar problems, but i did get the internet working fine useing wvdial with that install. Now this a new computer and i have hoary cd's which came in the post, so i thought double boot with win xp on my 3 gig pentium 4, all seemed fine, before on warty i had heaps of problems , i could connect to the internet with ppp but it was hopelessly slow,but withwvdial it worked as good as windows.
Now at first with hoary i tried just going to network and typing in user name dial up number and password and it detected my modem on devttyo. clicked on activate and it dialed up perfectly fast as dial up goes, ll happy. so i started updating programs i typed at a terminal apt-get update and away it went, since it takes many hours to update i left it running overnight, when i came in ,in the morning it said some updates could not be retireved. now when i dial up my internet connection has become incredibly slow like it was in warty, i have tried wipeing it off and starting again but still slow.
so i tried wvdial and it says no modem detected.
anyone help with this mess?[/QUOTE]


Did you do a hard reboot?

---

### Post by porsher_puddles on 2005-10-02
i have been searching through the many posts and i tried this,

charles@ubuntu:~$ sudo wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 56000
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Port Scan<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Port Scan<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Port Scan<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Port Scan<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Port Scan<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Port Scan<*1>: S42  S43  S44  S45  S46  S47  S48  S49
Port Scan<*1>: S50  S51  S52  S53

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
charles@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
charles@ubuntu:~$
obviously i haven't configured something right, but i don't know what to do, i can see it is detecting my modem.
can someone please explain in simple step by step terms what to do.
ty

---

