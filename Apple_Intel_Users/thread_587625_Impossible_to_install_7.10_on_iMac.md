---
title: "Impossible to install 7.10 on iMac"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by windowsesunamierda on 2007-10-22
Hi, I was using OS X 10.4 and Ubuntu 7,04.
When 7.10 came out I download it and tried to install it.

The boot screen from the CD went OK. I selected "Start or Install Ubuntu" (or something like that, but was the first option). It started loading fine until an error message appeared in the black (like the old DOS) screen:

[ 159.532000] bcm43xx: Error: Microcode "bcm43xx_microcode5. fw not available or load failed

and the same text appeared but with other numbers at the bigining

[ 181.568000]
[ 203.604000]
and so on...

Then, it shows a blue screen and a new message:

The Display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again o display :O.

then again the first error message (the one with [ numbers].
Then I reboot, try again, and the same thing.

After that, I tried with de "Graphic safe mode" but it was the same thing.
Finally I tried with the Alternate CD and this was interesting:
It loaded OK, it installed OK and ask  me for a reboot (normal until now). Then I reboot and... The same 2 errors on my screen.
I don't know what to do. Help me!!!

One interesting thing is that after all this I wanted to install 7.04 back but guess what, I also get the same 2 errors. This was really weird, because I never had that problem on April when I installed 7.04 for the first time.

A few things about my computer:
iMac Core Duo 1.83
Display card: ATI RADEON X1600 (I guess is MOBILITY, but I'm not sure).
Plus I haven't installed a firmware or something like that on my computer after the first 7.04 installation, so nothing weird there.

Something similar happened to this guy: [http://ubuntuforums.org/showthread.php?p=3572526](http://ubuntuforums.org/showthread.php?p=3572526)

Please, I really need help.

---

### Post by cyberdork33 on 2007-10-22
xorg is failing to start (ignore the bcm43xx errors). When you get to the blue screen, you can get to a console by typing CTRL+ALT+F1

At this point you can login, and edit the /etc/X11/xorg.conf file to use the vesa driver, then you can save and restart and you should get things up and running. after that you will want to install fglrx for your ATI card.

---

### Post by windowsesunamierda on 2007-10-23
> **cyberdork33 said:**
> xorg is failing to start (ignore the bcm43xx errors). When you get to the blue screen, you can get to a console by typing CTRL+ALT+F1

At this point you can login, and edit the /etc/X11/xorg.conf file to use the vesa driver, then you can save and restart and you should get things up and running. after that you will want to install fglrx for your ATI card.

Hi, I'm a native mac user, that means I have no idea what are you talking about.
Please, tell me step by step, what I have to do. Thanks

---

### Post by cyberdork33 on 2007-10-23
> **windowsesunamierda said:**
> Hi, I'm a native mac user, that means I have no idea what are you talking about.
Please, tell me step by step, what I have to do. Thanks

Do CTRL+ALT+F1

login

edit the /etc/X11/xorg.conf file (You can use several editors to do this, but nano is easiest). You have to have root permissions to edit this file so we must prepend the command with sudo:
```
sudo nano /etc/X11/xorg.conf
```

This this point find the section that sets up the video card. It should have a line that specifies a driver (Likely 'ati') change the currently set driver name to "vesa". Save the file (CTRL+X then answer Y). 

Restart (this also requires root permissions) (sudo restart)

---

### Post by windowsesunamierda on 2007-10-23
Hi, I did what you told me to, but when I open and look for the driver, it already says "vesa". Here is what I fond on the "Device" section without editing the file:

Section   "Device"
               Identifier     "Tarjeta de vídeo genérica" (which means "generic video card")
               Driver           "vesa"
               BusID           PCI:1:0:0"

So, because it already said "vesa" I couldn't solve my error, because obviously this isn't the error.
One interesting thing I tried is I change the Identifier to "ATI" (just to see what happens), save the file and reboot it. Then, when booted back tells me that it couldn't find a bootable disk because sda4 wasn't, or something like that.
Please, if somebody knows any solution I'll be much appreciated.

---

### Post by cyberdork33 on 2007-10-24
> **windowsesunamierda said:**
> 
One interesting thing I tried is I change the Identifier to "ATI" (just to see what happens), save the file and reboot it. Then, when booted back tells me that it couldn't find a bootable disk because sda4 wasn't, or something like that.
Please, if somebody knows any solution I'll be much appreciated.

That change would not cause that problem... there must have been something else done.

---

### Post by mikezila on 2007-10-24
I have an Intel iMac, and I get this same problem.

Easy fix for me.  When you get to the "Start or Install Ubuntu" screen, with all of the options, tap F4 and select 1024x768x32, and everything will start and work as you would expect it to.

---

### Post by windowsesunamierda on 2007-10-26
> **mikezila said:**
> I have an Intel iMac, and I get this same problem.

Easy fix for me.  When you get to the "Start or Install Ubuntu" screen, with all of the options, tap F4 and select 1024x768x32, and everything will start and work as you would expect it to.

Hello. I did what you told me to but it didn't work.
Instead of getting the blue screen with the display server error, I get a black screen with nothing on it but the cursor (not the mouse, the console cursor) on the upper left of the screen.
I can't type anything but if I type sudo reboot I can reboot my computer. You have to understand that when I type sudo reboot I can't see if I'm typing it or not.
Plus, if I press Ctrl+Alt+F1 it doesn't appear the console, just keep the mentioned black screen.
So if anyone else can help me I'll be really appreciated.
Thanks.

---

### Post by cyberdork33 on 2007-10-26
> **windowsesunamierda said:**
> Hello. I did what you told me to but it didn't work.
Instead of getting the blue screen with the display server error, I get a black screen with nothing on it but the cursor (not the mouse, the console cursor) on the upper left of the screen.
I can't type anything but if I type sudo reboot I can reboot my computer. You have to understand that when I type sudo reboot I can't see if I'm typing it or not.
Plus, if I press Ctrl+Alt+F1 it doesn't appear the console, just keep the mentioned black screen.
So if anyone else can help me I'll be really appreciated.
Thanks.
yea you definitely have video issues. You need to get the mode back to how it was so that you can at least see the terminal, then you can install the fglrx driver.
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo depmod -a[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]
```
then restart
[/FONT]

---

### Post by windowsesunamierda on 2007-10-26
Finally!!! Thank you cyberdork33, you made me happy :)
I can now use Ubuntu 7.10
I now have one little question: I enabled the ATI restricted drivers but couldn't activate the desktop effects. I get the "The Composite extension is not available" message error.
My xorg.conf file says the following:

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Tarjeta de vídeo genérica"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Tarjeta de vídeo genérica"
	Monitor		"Color LCD"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

What do I have to do to enjoy the desktop effects?
Thank you

Remember, I have an ATI Radeon Mobility X1600

---

### Post by cyberdork33 on 2007-10-26
the fglrx driver in the repos does not support compositing (actually, only the very last release does).

you can install the newer driver (not really recommended) or you can install XGL to provide the compositing.

```
sudo aptitude install xserver-xgl
```

Remember to restart again

---

### Post by windowsesunamierda on 2007-10-27
Thanks for the info. But why isn't recommended the newest drivers? Another question, that command that you told me, sudo aptitude ... is the same thing if I go to Synaptic, search for "xgl" and install the one that says "xserver-xgl"?
Again, thanks

---

### Post by cyberdork33 on 2007-10-27
> **windowsesunamierda said:**
> Thanks for the info. But why isn't recommended the newest drivers? Another question, that command that you told me, sudo aptitude ... is the same thing if I go to Synaptic, search for "xgl" and install the one that says "xserver-xgl"?
Again, thanks

yes but opening a terminal and typing a command seems faster to me, but you can use whatever manager you like.

The newest drivers have some issues. If you want to go ahead and try, here are the instructions:
[http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/](http://www.rickycampbell.com/2007/10/24/fglrx-8423-in-64bit-gutsy/)

---

### Post by bryan4134 on 2007-10-27
> **mikezila said:**
> I have an Intel iMac, and I get this same problem.

Easy fix for me.  When you get to the "Start or Install Ubuntu" screen, with all of the options, tap F4 and select 1024x768x32, and everything will start and work as you would expect it to.


Hi I am having the same Video problem - but when I tap F4 I do not have a 1024x768x32 option - the closest I have is a 1024x768x24 which I tried - same result....  

Any ideas appreciated...

Bryan

---

### Post by Ikzann on 2007-10-27
I can't install either; it gives me the same problem. When I try to install in text mode, it goes up to the partitioning stage and then says "The FATs don't match." When I ignore that, it then gets an error about writing to the partition I chose (which I designated to be formatted). I know it's the right partition; I checked with diskutil list.

---

### Post by windowsesunamierda on 2007-10-27
Hello people, I have no idea on linux so I can't help you. But one thing I can say: read all the things that cyberdork33 told me to and try it. The only one that went right for me and fixed my error was the last one:

Install with the alternate CD, reboot, when you get the display server error do CRL+ALT+F1 to go to the console, then do (with the Ubuntu CD in and Internet connection on):

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo depmod -a

and restart (sudo reboot)

I hope that work right for you too bryan4134 and Ikzann
Bye

---

### Post by Ikzann on 2007-10-27
Actually I tried installing using the DVD's text mode - it worked this time, using the instructions for fixing the video above. Thanks! I'm posting this from Gutsy right now. :D

---

### Post by AlainJLEB on 2007-11-27
Hi there,

I'm also trying to install fglrx on my iMac 24" (new one with ATI Radeon HD 2600 PRO), but when running the aticonfig --initial, it ends in a core dump:
```
alain@imac:~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-2
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbfd06aba ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d2192b]
aticonfig[0x805c5c7]
aticonfig[0x805c875]
aticonfig[0x8054528]
aticonfig[0x804985e]
aticonfig[0x80496cb]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7cca050]
aticonfig[0x8049601]
======= Memory map: ========
08048000-08067000 r-xp 00000000 08:03 7192584    /usr/bin/aticonfig
08067000-0806a000 rw-p 0001e000 08:03 7192584    /usr/bin/aticonfig
0806a000-0808b000 rw-p 0806a000 00:00 0          [heap]
b7ca6000-b7ca7000 rw-p b7ca6000 00:00 0
b7ca7000-b7ca9000 r-xp 00000000 08:03 9044942    /lib/tls/i686/cmov/libdl-2.6.1.so
b7ca9000-b7cab000 rw-p 00001000 08:03 9044942    /lib/tls/i686/cmov/libdl-2.6.1.so
b7cab000-b7cac000 rw-p b7cab000 00:00 0
b7cac000-b7cb0000 r-xp 00000000 08:03 345438     /usr/lib/libXdmcp.so.6.0.0
b7cb0000-b7cb1000 rw-p 00003000 08:03 345438     /usr/lib/libXdmcp.so.6.0.0
b7cb1000-b7cb3000 r-xp 00000000 08:03 345427     /usr/lib/libXau.so.6.0.0
b7cb3000-b7cb4000 rw-p 00001000 08:03 345427     /usr/lib/libXau.so.6.0.0
b7cb4000-b7df8000 r-xp 00000000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7df8000-b7df9000 r--p 00143000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7df9000-b7dfb000 rw-p 00144000 08:03 9044939    /lib/tls/i686/cmov/libc-2.6.1.so
b7dfb000-b7dfe000 rw-p b7dfb000 00:00 0
b7dfe000-b7e21000 r-xp 00000000 08:03 9044943    /lib/tls/i686/cmov/libm-2.6.1.so
b7e21000-b7e23000 rw-p 00023000 08:03 9044943    /lib/tls/i686/cmov/libm-2.6.1.so
b7e23000-b7f10000 r-xp 00000000 08:03 345423     /usr/lib/libX11.so.6.2.0
b7f10000-b7f14000 rw-p 000ed000 08:03 345423     /usr/lib/libX11.so.6.2.0
b7f14000-b7f21000 r-xp 00000000 08:03 345440     /usr/lib/libXext.so.6.4.0
b7f21000-b7f22000 rw-p 0000d000 08:03 345440     /usr/lib/libXext.so.6.4.0
b7f22000-b7f23000 rw-p b7f22000 00:00 0
b7f23000-b7f2a000 r-xp 00000000 08:03 345462     /usr/lib/libXrender.so.1.3.0
b7f2a000-b7f2b000 rw-p 00006000 08:03 345462     /usr/lib/libXrender.so.1.3.0
b7f2b000-b7f30000 r-xp 00000000 08:03 345460     /usr/lib/libXrandr.so.2.1.0
b7f30000-b7f31000 rw-p 00005000 08:03 345460     /usr/lib/libXrandr.so.2.1.0
b7f34000-b7f3e000 r-xp 00000000 08:03 9011267    /lib/libgcc_s.so.1
b7f3e000-b7f3f000 rw-p 0000a000 08:03 9011267    /lib/libgcc_s.so.1
b7f3f000-b7f42000 rw-p b7f3f000 00:00 0
b7f42000-b7f5c000 r-xp 00000000 08:03 9011213    /lib/ld-2.6.1.so
b7f5c000-b7f5e000 rw-p 00019000 08:03 9011213    /lib/ld-2.6.1.so
bfcf2000-bfd07000 rw-p bfcf2000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any idea why? And more important maybe: how can I install this driver, so that I can leave that slow vesa driver ?

Alain

---

### Post by cyberdork33 on 2007-11-27
Please do not double post...
I answered in your other thread:
[http://ubuntuforums.org/showpost.php?p=3849965&postcount=8](http://ubuntuforums.org/showpost.php?p=3849965&postcount=8)

---

