---
title: "Getting black and white flickering screen at startup (first install)"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2006-02-03
Hi there this is my fiirst install of Ubuntu on my laptop;

myhardware:

HP Compaq nw8240
80GIG HDD
Centrino Dothan 780
Graphics ATI FireGL 128MB (res 1920x1200)

During the installtion process Ubuntu asked me to choose the resolution I want X to use; naturally I figured that 1920x1200 (since it was listed) would be the best option. That;s the only one I chose.

Now when I try to get to the login screen I get this wiered balck and white lines horizontal, and sometimes the screen goes completely white.

I have tried cycling through X by ctrl+Alt+Backspace, but amd unable to to get this right.

I think I have messed up my screen for some reason?? I am very new to Linux, so please help me get out f this; Also note when I reboot into WinXP, the screen works fine.

Thanks,

Do I renstall Ubuntu and if I do what do I select as my resoution? i.e. safest one to get the GUI going; then how to get X.org to set my scren resolution?

I have read around a bit, so am familiar with some ways, but still learning quickly.

Please help!

---

### Post by shuttleworthwannabe on 2006-02-04
Was wondering if there was anyone to help me here.

---

### Post by shuttleworthwannabe on 2006-02-04
Hi there, I have been working on this problem th whole night; I figured out how to get the xserver-xorg reconfigured and I then set the graphics card to VESA to allow me to at least get beyond the CL and into the GUI login. I am in now, and this is what my X11/xorg.cong file reads:
===
Section "Device"
	Identifier	"ATI"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

===

I have also been to the ATI website to get a driver for this laptop graphics card:
ATI Mobility FireGL V5000; but am unable to get the driver installed even after following the instructions here: [http://www2.ati.com/drivers/linux/linux_8.16.20.html#176980](http://www2.ati.com/drivers/linux/linux_8.16.20.html#176980)

when I type ./ati-driver-installer-8.21.7-i386.run

I get this error:
==
sk@ubuntu:~$ sudo ./ati-driver-installer-8.21.7-i386.run
sudo: ./ati-driver-installer-8.21.7-i386.run: command not found
==

Could some PLEASE help me get going even further or tell me that I am not working in the right direction.
begging...
S

---

### Post by editrix on 2006-02-04
[QUOTE=shuttleworthwannabe]Could some PLEASE help me get going even further or tell me that I am not working in the right direction.
begging...
S[/QUOTE]

When I saw your subject line the first time, I wondered if I could help, but when I read the post, I doubted it. However, I understand the frustration of no one responding (it always means we don't have an answer, not that we don't care) so here's an answer:

I too have a "flickering" problem until I get to the login screen. It has to do with the monitor, not any programming, as I have the same problem in DOS, and no problem with a different monitor.

So I can't help at all except to suggest that you try a different monitor or try your monitor in DOS, if you can.

---

