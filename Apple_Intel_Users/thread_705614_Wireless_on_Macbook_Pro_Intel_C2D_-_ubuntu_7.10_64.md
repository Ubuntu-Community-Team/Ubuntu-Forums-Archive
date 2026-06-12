---
title: "Wireless on Macbook Pro Intel C2D - ubuntu 7.10 64"
date: 2008-02-23
forum: Apple Intel Users
---

### Post by tiagovsantunes on 2008-02-23
I have this type of wireless card: Wireless Card Type:	AirPort Extreme, but my network window in Ubuntu doesn't recognise the wireless possibility, only through ethernet cable.
Any idea of what might be missing?
Thank you in advance
Tiago

---

### Post by cyberdork33 on 2008-02-23
What is the output of lspci? This will help me direct you to the appropriate guide.

---

### Post by bubujake on 2008-02-23
You should have little problem if you can do the following:

1. You can search Google for your: Wireless Airport Extreme ...and actually find drivers for Debian/Ubuntu

2. You know how to do the apt install command, or you may have to do a "make install" and compile the C++ source, if the drivers are in that form.

3. You have to be able to select the new drivers "Airport Extreme" and bind it to device eth1 probably.

4. This is the kicker: If your laptop has a kill-switch for your wireless, you may run into a problem getting anything to work becuase of that, Linux sometimes has a problem initializing WiFI when there is a kill-switch.

Google searching is the way to go, but I had a kill switch on my laptop and even though I found the right drivers, I couldn't get it to work due to the kill-switch.

---

### Post by tiagovsantunes on 2008-02-24
Cyberdork33, here's my lspci output, thanks for your help:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

Bubujake, I installed a debian package with a bcm43xx driver, and nothing seemed to have happen. Maybe I'm way off... Thanks for your help, I'll keep on googling!

---

### Post by tiagovsantunes on 2008-02-24
UPDATE

So after googling some more I came across two programs that I could use:

madwifi and ndiswrapper

I tried madwifi first. The installation went well without any trouble, however, trying the command ifconfig showed me that the wireless card wasn't installed.

I tried ndswrapper afterwards (withouth uninstall madwifi so I don't know if that might be the problem). The installation went ok, and the windows driver installation went sort of ok (it showed this message: forcing 256 to 64). The windows drivers are only 32 bits...
But in the end I got this information: driver installed /device present which seems good... However the command ifconfig was still stating that the wirless card wasn't installed

I ran out of ideas to do. Any thoughts?

---

### Post by cyberdork33 on 2008-02-24
You have the Santa Rosa Macbook Pro. The wiki page for your machine is here:
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)

You have an Atheros-based Wi-Fi card. (Apple uses different cards and labels them all as "Airport Extreme". You should use Madwifi.

---

### Post by tiagovsantunes on 2008-02-24
I tried that tutorial, with Madwifi. Unfortunetly it didn't work. Doesn't show any wireless card on the ifconfig command...
I guess I have to buy a big ethernet cable.
Thanks
Tiago

---

### Post by mabovo on 2008-02-25
So easy to give up ? Try Hardy :)

---

### Post by cyberdork33 on 2008-02-25
> **mabovo said:**
> So easy to give up ? Try Hardy :)Yea if you are expecting everything to just work in linux, you will be disappointed more than once. If you want to get Ubuntu running well, you have to be willing to tinker around a little, ask questions, try new things. If you don't want to do that, I would wait until some of the kinks are worked out before installing Ubuntu on your machine.

---

### Post by rytmisk on 2008-02-27
I just want to confirm that this is a relevant issue. I have a new macbook pro too, and have not been successful in installing the wireless drivers (yet) - despite having solved similar problems on senveral other pcs over the years. (This is with hardy btw)

I can live with osx for the time being though since I have other pc´s to use rosegarden etc on, but it is kind of annoying
Ketil

---

### Post by cyberdork33 on 2008-02-27
> **rytmisk said:**
> I just want to confirm that this is a relevant issue. I have a new macbook pro too, and have not been successful in installing the wireless drivers (yet) - despite having solved similar problems on senveral other pcs over the years. (This is with hardy btw)
There are madwifi drivers that work, you just have to get the right revision... Support for the AR5418 chipset seems to come and go.

Be sure to blacklist the ubuntu modules in /etc/default/linux-restricted-modules-common

---

### Post by rytmisk on 2008-02-27
Hm the blacklist thing seems to be a common thing when it comes to driver configuration on linux. Do you have the exact line to insert?

Best regards
Ketil

---

### Post by cyberdork33 on 2008-02-27
> **rytmisk said:**
> Hm the blacklist thing seems to be a common thing when it comes to driver configuration on linux. Do you have the exact line to insert?

Best regards
Ketil
It is pretty easy once you open the file...

You need to add "ath_hal" in the section for modules to disable (This is the same as the proprietary module name). This will prevent the Ubuntu provided version from loading, and load your compiled version instead.

See the top of this page:
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

---

### Post by rytmisk on 2008-02-28
Many thanks to you!

Now for some more testing:-)

Ketil

---

### Post by hellmitre on 2008-03-01
[http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/](http://ubuntu-tutorials.com/2007/10/24/how-to-enable-wireless-networking-on-the-macbook-ubuntu-710/)

That oughtta work just fine. I have installed Ubuntu 7.10 a few times on this and each time did just that. It works every time, pretty well, too. Good luck.

---

### Post by cvasilak on 2008-03-01
I don't know if you have succeeded with the latest svn version of madwifi drivers, but for myself which i got the same card as you do 

03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

I got it working with the version madwifi-ng-r3122  and I never looked back.
You can get it from [http://snapshots.madwifi.org/madwifi-ng/](http://snapshots.madwifi.org/madwifi-ng/)

Hope it helps,
Christos

---

