---
title: "Xserver and gdm issues"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2007-03-20
Hi,

I have a peculiar problem.  I tried to install beryl and everything seemed to have gone fine.  However it doesn't seem to be working on my system.  I took a backup of the  /etc/X11/xorg.conf file. ( I am not sure if the system did that or I manually took the backup).  Anyway I had the backup file, so I replaced the modified xorg.conf file with the backup.  

Now the xserver (gdm) gives error everytime I boot.  The screen goes blank and after a few seconds a error message appears.  It is something like this:

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux vijay-Desktop 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 20 20:17:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
Error in I830WaitLpRing(), now is 1895754633, start is 1895752632
pgetbl_ctl: 0x1ffe0001 pgetbl_err: 0x49
ipeir: 0 iphdr: 54b00007
LP ring tail: a8 head: 144 len: 1f001 start 0
eir: 0 esr: 10 emr: ff7b
instdone: ffc1 instpm: 0
memmode: 0 instps: 424
hwstam: fffe ier: 2 imr: 53c iir: 80
space: 148 wanted 152

Fatal server error:
lockup

```

I reboot the system and select the recovery mode option from the grub menu.  And at the command prompt, I do a ```
sudo gdm 
```and manually start the xserver and it works fine.  Then again I reboot immediately and select the normal option and the error doesnot appear.  It happens only on my first boot and it continues as long as I donot start the gdm manually. 

I did ```
sudo dpkg-reconfigure xserver-xorg
``` but that didn't help.  I have been searching the forums for sometime but couldn't find a solution.

I am attaching the log files one when the error occured and the other when I manually restarted gdm.

---

### Post by zvacet on 2007-03-21
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by sunexplodes on 2007-03-21
Might be worth a try:

sudo dpkg-reconfigure gdm

---

### Post by vijayanand_sodadasi on 2007-03-23
Thanks zvacet and sunexplodes.  I will try those.

---

