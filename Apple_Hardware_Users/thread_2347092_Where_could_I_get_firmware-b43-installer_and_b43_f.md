---
title: "Where could I get firmware-b43-installer and b43 for ibook powerpc ?"
date: 2016-12-21
forum: Apple Hardware Users
---

### Post by mrj22 on 2016-12-21
Hi All,
   Currently I cleaned up my ibook g4 PowerPC and installed Ubuntu 10.04 PowerPc version on it, it works normal except no wifi connection.
I searched on the internet for a while invalid. I got a file b43-fwcutter_012_1build1_powerpc.deb, and tried to install it by sudo dpkg -i b43*deb , but it got errors
since no network connection.  I have tried to find a file broadcom-wl*bz2 , there is always not a right one -- they seem not a powerpc version ! How could I get the right
ones for ibook powerpc ? many thanks for solutions !

I type lspci -vnn | grep 14e4  it shows a message below

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

and dmesg shows huge volume of message (skipped)

---

### Post by mrj22 on 2016-12-22
I used the command sudo dpkg -i b43-fwcutter_012-1build1_powerpc.deb in Console, it echoed back the following messages:
(Reading database ... 102912 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:012-1build1 (using b43-fwcutter_012-1build1_powerpc.deb) ...
Unpacking replacement b43-fwcutter ...
Setting up b43-fwcutter (1:012-1build1) ...
--2016-12-22 12:52:58--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `downloads.openwrt.org'
dpkg: error processing b43-fwcutter (--install):
 subprocess installed post-installation script returned error exit status 4
Processing triggers for man-db ...
Errors were encountered while processing:
 b43-fwcutter

Here, the file wl_apsta-3.130.20.0.o is in the same directory with b43-fwcutter_012-1build1_powerpc.deb in my ibook

However dpkg still tried to look at that file from internet, which is not available in my ibook -- that generated errors.

How could I use local object file wl_apsta-3.130.20.0.o instead of the internet one to install b43-fwcutter_012-1build1_powerpc.deb successfully ?
Thank you a ton !!!

---

### Post by Bashing-om on 2016-12-22
mrj22; Ouch !

The thing here is that release 10.04 is long out of support . The software repository no longer exists .
Install a current release to obtain support for your issues and we will be glad to guide and assist.

[INDENT][INDENT]pending
[INDENT][INDENT][INDENT]what ya want to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

