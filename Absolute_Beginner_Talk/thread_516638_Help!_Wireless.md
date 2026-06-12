---
title: "Help! Wireless"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2007-08-03
I've installed Ubuntu as dual-boot with winXP on my Dell Latitude D600 and, to quote McDonald's, "I'm lovin' it!"

Most of my hardware has been recognised and works, including my display, sound, and ethernet have worked, but I am having one big problem: when I try to connect to my wireless network (it uses WEP encryption) it cannot find it or connect. I have tried to use Firefox but can't get the page loaded. I can send you info about my system but I may take a while as I have to dual-boot.

I think my card is a Dell TrueMobile 1400 a/b/g

---

### Post by Bachstelze on 2007-08-03
> **fraser_m said:**
> I think my card is a Dell TrueMobile 1400 a/b/g

Well, let's find out for sure ;) Open a terminal, type *lspci* and paste what you get.

---

### Post by dca on 2007-08-03
I think the Dell TruMobile is an Intel card so it may have been installed and ready for use w/ the restricted drivers module (ipw2200/3945)...  Double-check in: ->system ->administration -> network and see if it references there...
 
Yeah, if not, do the lspci command....

---

### Post by stchman on 2007-08-03
Intel wireless cards are supported very well in Ubuntu.  The new 4965 is not however.  Your card should be.

Have you tried clicking on the network manager icon to see if there are active wireless networks.

---

### Post by fraser_m on 2007-08-03
Here are the contents of *lspci*:

```
fraser@fraser-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 

01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 

01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 

01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio 

Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)
fraser@fraser-laptop:~$
```

Is this what you wanted to see?

---

### Post by dca on 2007-08-03
Hmmm, Broadcom 4309 chipset....
 
I guess that would make sense, the Dell 1350 was BCOM4306...
 
wait a sec...

---

### Post by ev5unleash1 on 2007-08-03
Try putting the information of your wireless network in manually and disable roaming mode. I've had to do this because the roaming mode did not work with me.

---

### Post by dca on 2007-08-03
Isn't the BCM43xx driver installed by default?
 
[http://ubuntuforums.org/showthread.php?t=185650](http://ubuntuforums.org/showthread.php?t=185650)

---

### Post by Bachstelze on 2007-08-03
If you're connected with your wired connection : 

```
sudo apt-get install bcm43xx-fwcutter
sudo iwconfig
```

Your wireless interface should appear.


> **dca said:**
> Isn't the BCM43xx driver installed by default?

Yes, but it needs a firmware to work, thus the installation of *bcm43xx-fwcutter*.

---

### Post by fraser_m on 2007-08-03
I cannot connect to a wired connection. Sorry!

Is there any way to do this without internet? e.g. from windows to ubuntu?

---

### Post by Bachstelze on 2007-08-03
Download those two files in Windows and copy them to your desktop in Ubuntu :

[http://fr.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-1_i386.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-1_i386.deb)
[http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)

Then

```
sudo dpkg -i ~/Desktop/bcm43xx-fwcutter_006-1_i386.deb
```

When the package will be installed, it will try to download a file and fail. Ignore it and do 

```
mv ~/Desktop/wl_apsta.o /tmp
cd /tmp
bcm43xx-fwcutter wl_apsta.o
sudo mkdir -p /lib/firmware
for i in *.fw; do
sudo mv $i /lib/firmware/$i;
done
rm wl_apsta.o
```

Then, reload the driver :

```
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx
```

and your wireless interface should appear when you do

```
sudo iwconfig
```

---

### Post by fraser_m on 2007-08-03
I am connected to the ethernet...

and...

IT WORKS!!!

Thanks everyone!

What's the quickest way to wipe an xp partition?!?!

---

### Post by Bachstelze on 2007-08-03
Using GParted from the official GParted Live CD

[http://gparted.sf.net](http://gparted.sf.net)

---

### Post by RAZZ on 2007-08-03
I had the same problem, so I did what HymnToLife said (I have a wired connection), and it seems to have worked. Yay! However, I am a little confused about the output of *sudo iwconfig*:```
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```The card is a 4309, not 4306. Is it still OK?

Also, is there a way to see available wireless networks, like in Windows XP?

Thanks!

---

### Post by st33med on 2007-08-03
To your first question, yes, it should be fine if it is working.

Next question, to see available wireless networks in your area, left click the bars/two computers/whatever icon it is for network manager. It should display the networks that your wireless network connection.

You could also try to do this in the terminal: 
```
iwlist eth1 scanning
```

---

### Post by RAZZ on 2007-08-03
You have been a big help, thanks!

---

### Post by RAZZ on 2007-08-07
I finally have a chance to try connecting to a wireless network. Only problem is that I can't get it to connect...

The network shows up in the list when I left-click the icon with the two screens, but it will not connect. It is a free, public network, so it is not protected in any way, and I have no trouble connecting to it with Windows XP.

What should I do?

Thank you in advance

---

