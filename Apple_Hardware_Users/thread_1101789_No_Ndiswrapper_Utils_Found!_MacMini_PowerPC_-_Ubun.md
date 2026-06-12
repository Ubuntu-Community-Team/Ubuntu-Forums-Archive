---
title: "No Ndiswrapper Utils Found! MacMini PowerPC - Ubuntu 8.04.1 LTS (Hardy Heron)"
date: 2009-03-20
forum: Apple Hardware Users
---

### Post by 1O1 on 2009-03-20
Hi everybody, I've been trying to get this working for hours now, and decided to sign up here and see if i can get any help :D. 

What im trying to do is install Netgear Rangemax WPN111 Wireless adapter on my Mac Mini PowerPC. At first i tried using OpenSUSE 11.1 since its still suppoting powerpc users, but after installing i wasn't able to install ndiswrapper at all. So i switched to Ubuntu 8.04.1 LTS (Hardy Heron) since im a little more familiar with Ubuntu. I had no problems installing it, and using a Wired connection I was able to do a system update and install "ndiswrapper-common" (1.50-lubuntu1) from Synaptic Packet Manager. I already have all the files needed to install the drivers for WPN111 (ar5523.bin;netwpn111.inf;WPN111.sys). But when i try to install using the command ```
sudo ndiswrapper -i netwpn11.inf
``` it shows ```
Error: no ndiswrapper utils found!

```

I don't know what I'm doing wrong but i cant get it to work, i found these steps online but i dont know if they are right [LINK]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/"), I'm hoping somebody here knows the answer and can even tell me if the link i just put is correct or outdated. Thanks!:)

---

### Post by cyberdork33 on 2009-03-20
> **1O1 said:**
> Hi everybody, I've been trying to get this working for hours now, and decided to sign up here and see if i can get any help :D. 

What im trying to do is install Netgear Rangemax WPN111 Wireless adapter on my Mac Mini PowerPC. At first i tried using OpenSUSE 11.1 since its still suppoting powerpc users, but after installing i wasn't able to install ndiswrapper at all. So i switched to Ubuntu 8.04.1 LTS (Hardy Heron) since im a little more familiar with Ubuntu. I had no problems installing it, and using a Wired connection I was able to do a system update and install "ndiswrapper-common" (1.50-lubuntu1) from Synaptic Packet Manager. I already have all the files needed to install the drivers for WPN111 (ar5523.bin;netwpn111.inf;WPN111.sys). But when i try to install using the command ```
sudo ndiswrapper -i netwpn11.inf
``` it shows ```
Error: no ndiswrapper utils found!

```I don't know what I'm doing wrong but i cant get it to work, i found these steps online but i dont know if they are right [LINK]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/getting-netgear-wireless-usb-dongle-wpn111-atheros-chipset-to-work-on-ubuntu-6.06-515914/"), I'm hoping somebody here knows the answer and can even tell me if the link i just put is correct or outdated. Thanks!:)
install ndiswrapper-utils ;)

---

### Post by jdp on 2009-03-21
A PPC system cannot run the drivvers that NDISWrapper loads, even if NDISWrapper itself gets installed.  The point of NDISWrapper is to run compiled, binary only, drivers that are written for Windows.  The PPC Mac mini just cannot run those x86 drives.  Period.

---

### Post by marshag63 on 2009-03-21
I've had the same problem - just got it straightened out.

You need to get the compat-wireless-old.tar.bz2 and install it - it sets up wireless for PPC.  (I think I used the command "sudo make load") and it took care of installing/uninstalling what it needed.

Then, you also need to download zd1211-firmware-1.4.tar.bz2.  Download to your desktop and expand it, then extract to this directory:

lib/firmware/zd1211 

(its easier to expand to desktop and copy files to /lib/firmware/zd1211 - otherwise it expands and makes a subdirectory of zd1211 and you have to move the files back up one diretory to zd1211 anyway).

Then reboot, with you usb stick plugged in.

Good Luck!

MarshaG.

P.S. let us know if you got it figured out.

---

