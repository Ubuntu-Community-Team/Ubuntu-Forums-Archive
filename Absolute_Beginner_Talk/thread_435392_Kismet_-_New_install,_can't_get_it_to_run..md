---
title: "Kismet - New install, can't get it to run."
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by kouloubj on 2007-05-06
Hello all:

I'm new to Ubuntu and am trying to get Kismet to run.  I think i made the correct changes to the kismet.conf file but receive the following error when i attempt to run it..

laptop:  Dell D620
Wireless adapter:  Broadcomm:  Dell Wireless 1390 WLAN Mini-PCI Card

bill@laptop-tux:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Illegal card source line 'ethX'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
bill@laptop-tux:~$ 

any help would be greatly appreciated.

Thanks in advance!

---

### Post by jargoman on 2007-05-07
I gave up on kismet because I thought that broadcom didn't support monitor mode. I could be wrong though. It might just be my configuration but


~$ sudo iwconfig eth2 mode monitor

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

try the command if nothing happens it probably worked. You can verify with

~$ sudo iwconfig

some packet sniffing software requires you to put your card in monitor mode manually in this way

---

### Post by iskarion on 2007-05-08
I don't have much experience with Kismet, but I guess this is the source of your problem

> **kouloubj said:**
> FATAL: Illegal card source line 'ethX'

In the default kismet.conf ethX is used as an example. But I think you have to replace it with a real interface name like eth0, eth1 or something similar.

---

### Post by ttakun on 2007-05-08
Open a terminal window an type the **iwconfig** command. It will tell your wireless interface (eth0, eth1, ...)
Having a look at [Kismet Readme File]("http://www.kismetwireless.net/documentation.shtml#readme"), I hope you have in your kismet.conf bcm43xx as sourcetype.

As that readme file says, the drivers for Broadcom based wireless cards are in "experimental" state.

---

