---
title: "Cannot install 6.06 lts on old system"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Chipsterian on 2007-05-29
Hello everyone. First time posting here.

I am attempting to salvage some old computers I have at the office with Ubuntu.

The computers in question: ACER Veriton 5100, with all onboard connections. There are no cards in this box; 256 MB of RAM, 8GB hdd. Used to hold Windows 98 SE.

when installing v6.06, *(the iso I created this from is ubuntu-6.06.1-desktop-i386.iso)* the computer starts just fine. It shows the opening screen,I select start or install ubuntu, an it goes thru the checklist. It finishes the checklist and there is a brown-hued screen that sits there.

A ctrl-alt-bksp will restart the kernel and it then asks for a username, at which point I hit enter and the desktop pops up. It however, will not display an installation icon at this point.

I have successfully installed kubuntu, which doesn't help me much as the NIC and usb ports are not available. I have currently ubuntu 5.10 residing on the computer. The usb ports are available, the NIC is MIA, and the 3.5" floppy has eloped.

Help.
Chip.

---

### Post by DJ Wings on 2007-05-29
Use an alternate CD. I suggest Xubuntu, as opposed to Ubuntu, for older computers. And even it might not be the best idea... Check out [DeLi.](http://www.delilinux.de)

---

### Post by Chipsterian on 2007-05-29
Sorry, forgot to mention, the  CD has been successfully been installed on three other computers; two before and one after. These are not the Acer's tho.

As far as the new dells go, these have a price that so far beat a new dell, 13 acers for free. I want to not use win98 for them if I can.

---

### Post by DJ Wings on 2007-05-29
Still, see above post. Lighter distros that Ubuntu are worth a look.

---

### Post by Chipsterian on 2007-05-29
Okay, I now have Xubuntu on the computer. It is not networking, still.

What is needed to know to get this computer networked?

---

### Post by DJ Wings on 2007-05-29
If the network is wireless, post the output of "lspci -v".

---

### Post by Chipsterian on 2007-05-29
on-board LAN port, the device is a Intel Pro 100 VE.

No wireless cards installed.

lspci -v result: 01;08:0 Ethernet controller: Intell Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
Subsystem: Intel Corporation EtherExpress PRO/100 VE
Flags: bus master, medium devsel, latency 32, IRQ 9
Memory at 80101000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 74 [size=64]
Capabilities: ,access denied>

---

### Post by DJ Wings on 2007-05-29
Funny, I have a Pro/100, and it works fine on  Xubuntu...

---

### Post by Chipsterian on 2007-05-29
thats just it. This system worked fine when windows 98 was installed. But I'm in a  library, and that OS is non-secure.

This includes the onboard LAN.

Its the LAN I need working.

---

### Post by DJ Wings on 2007-05-29
Post the result of ```
sudo ifconfig.
```
Off-topic: 100th post.

---

### Post by Chipsterian on 2007-05-29
Congrats.

eth0
Link encap:Ethernet  HWaddr 00:00:E2:33:9A:AB
inet6 addr: fe08:200:e2ff:fe33:9aab/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo
Link encap:Local Loopback
inet addr: 127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128  Scope:Host
UP LOOPBACK RUNNING  MTU:16436 Metric:1
RX packets:160 errors:0 dropped:0 overruns:0 frame:0
TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueue:1000
RX bytes:12080 (11.7 Kib)  TX bytes:12080 (11.7 KiB)

---

### Post by Chipsterian on 2007-05-30
I think I stumped him.

---

### Post by compmodder26 on 2007-05-30
You network card is properly detected and running.  You just need to get an IP address for it.  Post the contents of /etc/network/interfaces

---

### Post by Chipsterian on 2007-05-30
contents of /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


after shutting the comp down overnight, the lspci -v and the contents of the interfaces file are unchanged.
Would it make a difference if I was connected to a wndows 2003 dhcp server, and if so why did it not affect the other ubuntu machines?

---

### Post by Chipsterian on 2007-05-31
Help!


*If bumping is against forum rules, this won't happen again...*

---

### Post by Chipsterian on 2007-06-04
To everyone who tried to come to my rescue, thank you.

I'm installing Win 2k on the machines, and living with those issues. At least I know them best.

---

### Post by ebaymic on 2007-07-02
I have recently obtained an Acer Veriton 5100 and came across the same mentioned problems with the live CD getting stuck in the Gnome Desktop boot screen. ;)

I have managed to find a work around to get the CD to load correctly.  Seems to be an issue with ACPI with this PC.  Have read that some Bois's are not totally compatible to Linux need the ACPI feature disabled.

To boot the Ubuntu or Linux Mint CD ( in my case) in the boot Menu I pushed the F6 Accessibility Key and then entered     acpi=off   .  This disables acpi in the kernel.

Once the operating system is installed Grub loader has to be changed.  In /boot/grub/menu.1st add or modify acpi=off  (may have to change it from "on")

title		Linux Mint, kernel 2.6.20-16-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=aff2d45f-d9c6-4352-89cf-f6cf42ad7c5e ro quiet splash acpi=off 
initrd		/boot/initrd.img-2.6.20-16-386
quiet

After that everything so far works.  Previously I could not get the sound card, Network Card  and USB ports to work.  Everything seem to be recognised  but did not do anything.

Hope that Helps.

---

