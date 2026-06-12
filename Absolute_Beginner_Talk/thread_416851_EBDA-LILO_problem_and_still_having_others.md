---
title: "EBDA-LILO problem and still having others"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by msfisher on 2007-04-21
Although I don't want to give up on Ubuntu, I'm getting close with this problem on top of the others I've had.  

I have a multiple boot Sempron 2600, 512megs memory, MSI motherboard with Nvidia nforce3 250 chipset, Nvidia Geforce2 MX400 video with 64megs, Realtek 8139 on-motherboard NIC set up as follows:

hda1,2&3 and hdb1  Windows 98SE, booting on hda1
hdb2  Xandros 3
hdb3  Ubuntu 6.10, Alternate CD install
hdb5  ext2, nothing loaded
hdb6  Linux swap

I'm a newbie to Ubuntu, but have tried out other Linux distros and have been a heavy MS user since before Windows was around.  

I use LILO as the boot manager.  After yet another effort to solve the problems I've written about previously (which failed), when I rebooted I got the following message:

EBDA is big; kernel setup stack overlaps LILO at second stage.

My lilo.conf is:

boot=/dev/hda
install=/boot/cboot.b
message=/boot/splash.lilo
timeout=300
map=/boot/map
prompt
lba32
read-only
compact
fix-table
other=/dev/hda1
	label=Windows_98
image=/vmlinuz
	label=Xandros_Desktop_3.0_Deluxe
	vga=0xf04
	root=/dev/hdb2
	initrd=/boot/initrd-2.6.9-x1.gz
	append="quiet rw acpi=on "
image=/vmlinuz
	label=Safe_Video_Mode
	vga=0xf04
	root=/dev/hdb2
	initrd=/boot/initrd-2.6.9-x1.gz
	append="quiet 3 rw acpi=on "
image=/disks/ubuntu/boot/vmlinuz-2.6.17-11-generic
	label=Ubuntu_6.10_on_hdb3
	initrd=/disks/ubuntu/boot/initrd.img-2.6.17-11-generic
	append="root=/dev/hdb3 ro quiet splash"
image=/vmlinuz
	label=Configure_(Expert)
	vga=normal
	root=/dev/hdb2
	initrd=/boot/initrd-2.6.9-x1.gz
	append="single quiet rw acpi=on noresume noresume2 "

I'm not up on LILO setup, so I'm not sure, but something doesn't look right with the Ubuntu entry.  Should it read like below?

image=/disks/ubuntu/boot/vmlinuz-2.6.17-11-generic
	label=Ubuntu_6.10_on_hdb3
	root=/dev/hdb3
	initrd=/disks/ubuntu/boot/initrd.img-2.6.17-11-generic
	append="ro quiet splash"

If not, what else might be wrong?  Xandros and Win98SE boot OK.  

Second, the problems I wrote about previously were still there when this new one happened.  Specifically, very slow startup after the login screen.  I log in, then get a totally empty desktop.  Ten seconds or so go by, then, since this was an Alternate CD install, mounted disk icons appear.  They are active.  Ten or fifteen seconds, then the GNOME panels appear, without icons.  Another ten or fifteen seconds and the icons appear, inactive.  Twenty or thirty seconds later, the icons become active, but opening applications takes an inordinately long time AND terminal does not completely open at all.  After ten or fifteen MINUTES, application opening times drop to more normal rates and the terminal can be opened.  

In spite of that, network speed remains distressingly slow.  BOTH Firefox and Ubuntu updates.  If I ping localhost, all looks OK -- ping times about 0.03ms to 0.04ms. When I try to ping my router, HUGE difference. First ping takes >1000ms, second about 25ms, third back to >1000ms, and repeating indefinitely.  I saw this behavior in Mandriva 2006 and 2007 as well.  

I've disabled ipv6 and made the corrections to the hosts file others have recommended, with no improvement.

ifconfig -a gave the following output

eth0 Link encap:Ethernet HWaddr 00:13:D3:9E:28:0D 
inet addr:192.168.2.102 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::213:d3ff:fe9e:280d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1324 errors:2 dropped:2 overruns:1 frame:0
TX packets:1294 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:932928 (911.0 KiB) TX bytes:194411 (189.8 KiB)
Interrupt:15 Base address:0xc000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

sit0 Link encap:IPv6-in-IPv4 
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

At this point, any help will be greatly appreciated, at least with the LILO problem (so I can get back into Ubuntu and see if the other problems can be fixed).

Many thanks in advance.

---

### Post by msfisher on 2007-04-27
Well, I plucked up my nerve and tried editing the lilo.conf.  It turned out that the idea I had in my original post solved that problem.

HOWEVER, the slow startup, slow application start and slow network are still there.

---

