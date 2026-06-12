---
title: "screen resolution"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by flewis on 2007-02-10
i have installed ubuntu, it works. the screen is not right I have 15.4inch wide screen (laptop monitor) i have tried the 

sudo dpkg-reconfigure xserver-xorg

went through it and set it up the way other post said to no luck in many different settings i reboot and I have to revert back to old xorg.conf file.

I also tried to edit the xorg.cong file itself still no luck. 

i don´t know what i am doing wrong i think it might be a driver issue not sure. I have no prior experience with os´s only windows.

i have a dual boot ubuntu with windows XP. on a Dell Ispiron E1505 laptop.

i pulled this info out of the xp side about my monitor

Name	Mobile Intel(R) 945GM Express Chipset Family
PNP Device ID	PCI\VEN_8086&DEV_27A2&SUBSYS_01BD1028&REV_03\3&61AAA01&0&10
Adapter Type	Intel(R) Calistoga Graphics Controller, Intel Corporation compatible
Adapter Description	Mobile Intel(R) 945GM Express Chipset Family
Adapter RAM	224.00 MB (234,881,024 bytes)
Installed Drivers	ialmrnt5.dll
Driver Version	6.14.10.4446
INF File	oem7.inf (i945GM0 section)
Color Planes	1
Color Table Entries	4294967296
Resolution	1280 x 800 x 60 hertz
Bits/Pixel	32
Memory Address	0xEFF00000-0xEFF7FFFF
I/O Port	0x0000EFF8-0x0000EFFF
Memory Address	0xD0000000-0xDFFFFFFF
Memory Address	0xEFEC0000-0xEFEFFFFF
IRQ Channel	IRQ 16
I/O Port	0x000003B0-0x000003BB
I/O Port	0x000003C0-0x000003DF
Memory Address	0xA0000-0xBFFFF
Driver	c:\windows\system32\drivers\ialmnt5.sys (6.14.10.4446, 1.30 MB (1,364,574 bytes), 1/23/2007 2:04 PM)
	
Name	Mobile Intel(R) 945GM Express Chipset Family
PNP Device ID	PCI\VEN_8086&DEV_27A6&SUBSYS_01BD1028&REV_03\3&61AAA01&0&11
Adapter Type	Intel(R) Calistoga Graphics Controller, Intel Corporation compatible
Adapter Description	Mobile Intel(R) 945GM Express Chipset Family
Adapter RAM	224.00 MB (234,881,024 bytes)
Installed Drivers	ialmrnt5.dll
Driver Version	6.14.10.4446
INF File	oem7.inf (i945GM1 section)
Color Planes	Not Available
Color Table Entries	Not Available
Resolution	Not Available
Bits/Pixel	Not Available
Memory Address	0xEFF80000-0xEFFFFFFF
Driver	c:\windows\system32\drivers\ialmnt5.sys (6.14.10.4446, 1.30 MB (1,364,574 bytes), 1/23/2007 2:04 PM)

my questions are 
How would i find out if my video driver is installed?
if not how would i install it?
I´m sure it is also user error some where on my part any sugestions?
i can use the terminal ok and I can figure out the boot command lines.  Any help is greatly apperciated

---

### Post by r4ik on 2007-02-10
Open Synaptic and try a search on i810.

Good luck !

---

### Post by veloce on 2007-02-10
I also have a Dell laptop with the 945GM card. You need:

[LIST]
[*]To get the higher resolutions the package "915resolution" installed. 
[*]Your graphics driver is an i810
[/LIST]
Using Synaptic Package Manager search for i810 and check that you have a driver installed. I'm pretty sure you will have.

Next search for "915" and you should see 915resolution.  Install this.

Easiest thing to do next is just to reboot.  If you are more adventurous (and know to use CTRL+ Alt+F1 to get a command prompt to reboot out of difficulty):

[LIST]
[*]Use AltF2 to bring up the run command window.  Run the command:
[*]sudo /etc/sbin/915resolution
[*]Close everything that you want to save and restart X windows "Ctrl + Alt + Bksp"
[/LIST]

Good luck.

---

### Post by r4ik on 2007-02-10
Good post thanks for the extra info.

---

### Post by caro on 2007-06-02
I wondered how to do this too.  Worked for me beautifully.  Thanks.

---

### Post by rambeaut69 on 2007-06-05
Thanks for the straightforward, easy on a newbie post.

---

