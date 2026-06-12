---
title: "Wireless-G (802.11g) WMP54GX4 installation problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Racer_D on 2008-02-27
I downloaded ubuntu 7.10 and am using Linksys adapter, Wireless-G (802.11g) WMP54GX4. Ubuntu is not detecting my wireless card at all. There are only two option in network connection.
1. wired connection
2. modem connection

i went to ubuntu website and downloaded the firmware from
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) but still no luck :(

please help....

---

### Post by sayakb on 2008-02-27
> **Racer_D said:**
> I downloaded ubuntu 7.10 and am using Linksys adapter, Wireless-G (802.11g) WMP54GX4. Ubuntu is not detecting my wireless card at all. There are only two option in network connection.
1. wired connection
2. modem connection

i went to ubuntu website and downloaded the firmware from
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy) but still no luck :(

please help....

Check whether you have the driver installed at the Restricted driver manager.

---

### Post by dca on 2008-02-27
Don't quote me on this but with that device so long as it's activated during install upon rebooting you should get a notice on your sys tray indicating that 'Restricted Drivers are in use'.  If not, with the device on and connected go (from the panel menu) 'System -> Administration -> Restricted Drivers Manager' and see if it lists the device...
 
If not, go to CLI and post the results of these commands:
 
lspci
lsusb
 
(that's a lower-case 'L')
The first command if it's an internal PCI card.
The second command if it's a USB external dealie.

---

### Post by Racer_D on 2008-02-27
thnx for the help. i went to the restricted driver but i can't see any networking thing. there is NVDIA accelerated graphics driver under the driver option..... nothing else..... by the way, wht is CLI

---

### Post by sayakb on 2008-02-27
> **Racer_D said:**
> thnx for the help. i went to the restricted driver but i can't see any networking thing. there is NVDIA accelerated graphics driver under the driver option..... nothing else..... by the way, wht is CLI

Open a terminal and type in:
lspci
lsusb

Edit: And post the output of these commands here.

---

### Post by Racer_D on 2008-02-27
ok.... i received the following message

racer@racer-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:02.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
racer@racer-desktop:~$

---

### Post by dca on 2008-02-27
> **Racer_D said:**
> ok.... i received the following message

racer@racer-desktop:~$ lspci

07:02.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)

racer@racer-desktop:~$

According to this, is it this card you're trying to get to work?
 
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01)
 
or this one?
 
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130279434670&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3467039789B07](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130279434670&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3467039789B07)

---

### Post by dca on 2008-02-27
...either way a lot of the evidence I see indicates you need to use the 'ndiswrapper' utility and the Windows drivers located on the install CD or Linksys website in order to get it to work...

---

### Post by Racer_D on 2008-02-27
wht do you mean by 'ndiswrapper' utility..... and the adapter i am using is
[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1122062238277&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3827739789B01)

---

### Post by Racer_D on 2008-02-27
Still no luck.... pls help

---

