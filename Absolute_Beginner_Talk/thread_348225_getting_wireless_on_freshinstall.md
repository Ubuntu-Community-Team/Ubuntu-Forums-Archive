---
title: "getting wireless on freshinstall?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by ELD on 2007-01-28
Hi i am still pretty new to linux, installed the latest ubuntu on my laptop and my internet is wireless.

How would i go about getting the net on my ubuntu partition?

Thanks a bunch guys.

---

### Post by Pobega on 2007-01-28
What is the output of this command:> lspci

---

### Post by ELD on 2007-01-29
> 
liam@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Sorry for late reply.

---

### Post by ELD on 2007-01-31
Bump

---

### Post by mikewhatever on 2007-01-31
Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Have tried System->Administration->Networking?

---

### Post by ELD on 2007-01-31
Th only options i get are wired and modem, there are no wireless options.

---

### Post by jkeyes0 on 2007-01-31
Sounds like the driver for your wireless card is not installed. If possible, plug your wired connection in, get it set up to connect to the net, then perform the following instructions (taken from [here]("http://www.ubuntuforums.org/showthread.php?t=345980&highlight=3945ABG")):

a) install the ipw3945 modules and firmware (search for "ipw3945" in synaptic)
b) apt-get install module-assistant
c) module-assistant update
d) module-assistant prepare
e) module-assistant auto-install ipw3945
f) modprobe ipw3945

Anytime you install a new kernel, you will need to go back through steps c-e.

Hope this helps.

Edit: This might also work (from the same thread mentioned earlier):
in etch:
apt-get install ipw3945-modules-2.6.18-3-YOUR-KERNEL

You will still have to get your wired connection working though.

---

### Post by ELD on 2007-01-31
Sounds like too much work for me, i will stick with windows.

---

### Post by saadakhtar on 2007-01-31
i looked at the results for lspci.
i think your driver is all set.
open terminal and then type in:

sudo ifdown wlan0
and you should see a bunch of lines once its done then type in:
sudo ifup wlan0
this time you will actually see the wlan card negotiating a connection with your router.
 cheers.

---

### Post by ELD on 2007-02-02
I got this:

> 
liam@ubuntu:~$ sudo ifdown wlan0
Password:
ifdown: interface wlan0 not configured
liam@ubuntu:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.


---

### Post by ELD on 2007-02-06
Bump

---

### Post by aseneca on 2007-02-06
Eh... windows isnt any fun!

Look at this.

[http://ubuntuforums.org/showthread.php?p=2090969](http://ubuntuforums.org/showthread.php?p=2090969)

AS

---

### Post by ELD on 2007-02-06
So i should get the kernel and restricted modules from feisty?

---

