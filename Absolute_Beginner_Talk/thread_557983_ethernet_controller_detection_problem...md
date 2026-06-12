---
title: "ethernet controller detection problem.."
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by game on 2007-09-23
i m new 2 d linux world..i hav internet workin on my windows but here on ubantu i m not able to detect my lan card and thus unable to access internet.
following is d output of comand ispci
pls i need help as soon as possible 
thank u



rohan@rohan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
02:00.0 Ethernet controller: Unknown device 1969:1048 (rev b0)
rohan@rohan-desktop:~$

---

### Post by Fitzy_oz on 2007-09-24
> **game said:**
> i m new 2 d linux world..i hav internet workin on my windows but here on ubantu i m not able to detect my lan card and thus unable to access internet.
following is d output of comand ispci
pls i need help as soon as possible 
thank u



rohan@rohan-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
02:00.0 Ethernet controller: Unknown device 1969:1048 (rev b0)
rohan@rohan-desktop:~$


Welcome!
If you woudn't mind just posting a little more about your motherboard/model - I suspect it is an ASUS borad of some kind and/or has an Attansic L2 ethernet card on it as they are the only onboard Ethernet adapter i have come across that isn't detected by Ubuntu straight up - Try this thread: [http://ubuntuforums.org/showthread.php?t=429845&highlight=attansic](http://ubuntuforums.org/showthread.php?t=429845&highlight=attansic)

---

### Post by game on 2007-09-25
yeah..my motherboard model is asus P5B-MX/WIFI-AP
and my lan is ATLANSIS L1 PCIE Gigabit lan controller..

---

### Post by Fitzy_oz on 2007-09-25
> **game said:**
> yeah..my motherboard model is asus P5B-MX/WIFI-AP
and my lan is ATLANSIS L1 PCIE Gigabit lan controller..

Ok - Download this driver
[http://ubuntuforums.org/attachment.php?attachmentid=33221](http://ubuntuforums.org/attachment.php?attachmentid=33221)

Unzip the archive and copy it to your modules directory like so, the numbers are the kernel versions, if you installed an update for it, it should be 20-16-generic, u can check this when you reboot next and come to the grub menu, just hit escape and it will tell you the version number it's booting.

sudo cp atl.ko /lib/modules/[COLOR="red"]2.6.20-15-generic[/COLOR]/kernel/drivers/net/atl.ko and then

sudo cp atl.ko /lib/modules/[COLOR="red"]2.6.20-16-generic[/COLOR]/kernel/drivers/net/atl.ko

then

sudo insmod /lib/modules/[COLOR="Red"]<KERNEL VERSION>/[/COLOR]kernel/drivers/net/atl.ko

Reboot and then you should be right

---

### Post by jcliburn on 2007-09-25
> **Fitzy_oz said:**
> Ok - Download this driver
[http://ubuntuforums.org/attachment.php?attachmentid=33221](http://ubuntuforums.org/attachment.php?attachmentid=33221)


That link pulls down an L2 driver (according to the filename, anyway), but the OP's ethernet device is an L1 [pci_id 1969:1048].

I'm not an ubuntu user, so I'm ignorant as to which kernel ships with which ubuntu, but I thought the atl1 driver was included in ubuntu 7.04.

---

### Post by Fitzy_oz on 2007-09-25
> **jcliburn said:**
> That link pulls down an L2 driver (according to the filename, anyway), but the OP's ethernet device is an L1 [pci_id 1969:1048].

I'm not an ubuntu user, so I'm ignorant as to which kernel ships with which ubuntu, but I thought the atl1 driver was included in ubuntu 7.04.

The module name is atl.ko and it's compiled from the manafacturers website - I'd wager that this device will run off that driver given theat it's called atl.ko not atl2.ko.  At any rate, it's not working period so it can't be any worse than it already is... :)

---

### Post by jcliburn on 2007-09-25
It's an L2 driver.  The pci_id for an L2 is 1969:2048.

[jcliburn@osprey ~]$ strings atl2.ko | grep 1969
alias=pci:v00001969d00002048sv*sd*bc*sc*i*

This driver won't work with an L1 NIC.

---

### Post by Fitzy_oz on 2007-09-25
> **jcliburn said:**
> It's an L2 driver.  The pci_id for an L2 is 1969:2048.

[jcliburn@osprey ~]$ strings atl2.ko | grep 1969
alias=pci:v00001969d00002048sv*sd*bc*sc*i*

This driver won't work with an L1 NIC.

I stand corrected - Apparently these nics are a real pain in the a***.

Heres a link for the source of the driver - I might compile the module when i get home and upload it, but if you want to try it yourself the link is there.  the installation process is the same as above once the device is compiled.

[http://downloads.sourceforge.net/atl1/atl1-2.0.7-linux-2.6.20-standalone.tar.gz?modtime=1171723995&big_mirror=0](http://downloads.sourceforge.net/atl1/atl1-2.0.7-linux-2.6.20-standalone.tar.gz?modtime=1171723995&big_mirror=0)

---

### Post by miceagol on 2008-01-20
Just experienced some problems with P5B-E and the Attansic/Atheros L1 LAN device after installing Vista on my system. After installing the drivers for the network device in Windows (I installed the newest august 2007 beta drivers for the card), the atl1 drivers for the card no longer worked in Ubuntu, and booting Vista now froze the system.

Apparently a new firmware or something was uploaded to the card after installing the newest drivers. The solution, beleive it or not, was to shut down the system, unplug the power cable and plug it back in. Seems like the firmware was removed from the card by cutting its power source. :)

This might have been your problem since the network device Attansic/Atheros L1 should work out of the box in Ubuntu 7.04 and later. Remember to install the network drivers from november 2006 in Vista/XP instead.

---

