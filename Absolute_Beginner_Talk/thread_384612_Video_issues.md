---
title: "Video issues"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-03-14
Ok. I've posted about this before, but done a fresh install since then with a different monitor, which sorted out the screen res problems, so I'll start again.
I have problems with the performance of my PC. It's a 1.4ghz celeron with 512mb RAM and a 64mb voodoo video card. Problems are:
Video performance is terrible. Even that video of Nelson Mandela in the examples folder plays jerkily. 
Windows move slowly when you drag them and leave a jerky trail.
zsnes, the nintendo emulator, is so slow it's unusable. My son loves this. Need to get it working.
I'm assuming its a graphics card driver issue. I've looked up the various 'glide' things in synaptic package manager, and tried installing anything that says 'use this if your have a voodoo 4/5 card' with no difference to performance.
Can anyone suggest anything else?

---

### Post by glenndavy on 2007-03-15
Hi There... I don't have a voodoo card, but just out of curiosity.. would you care to share your xorg.conf file... or at least the 'device' section?

---

### Post by Fidelio on 2007-03-15
I'd be happy to, but I don't know how to.
Also, I did notice that when I look at the device manager, there is another graphics device listed. This is a Cyberblade i1, which i think is the built in graphics on the mobo. Could this be causing the problem? I dunno, but maybe my installation detected this and is running drivers for it?
I can't seem to disable it in the bios, but I suppose there might be a jumper on the board. Or can I disable it from within linux like you can with the windows device manager?
My lspci:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia] (rev 05)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:08.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 4 / Voodoo 5 (rev 01)
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
```

---

### Post by glenndavy on 2007-03-15
yes... this is likely a problem

your xorg.conf is found in /etc/X11

(i.e. choose to attach a file and browse to /etc/X11/xorg.conf)

OR
simply browse to that file in your file manager and open it with text editor and cut and paste any section that looks like this:
```

Section "Device"
#stuff here
EndSection

```

---

### Post by Fidelio on 2007-03-15
Thanks,
Do you mean this bit?

S```
ection "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 4 / Voodoo 5"
	Driver		"vesa"
	BusID		"PCI:0:8:0"
EndSection
```

---

### Post by Fidelio on 2007-03-15
Ok so that VESA driver is just some kind of generic thing. SO I do have the wrong driver. The correct drivers are available, aren't  they. That's what all that glide, libglide and libgl1mesa-glide3 stuff is right?
So how do I force linux to use the correct driver?
???

---

### Post by glenndavy on 2007-03-16
ok  - first thing i've never played with voodoo, so i dont really know... but...

a quick google suggests you probably should replace "vesa" with "tdfx"

and perhaps do an

sudo apt-get install x-server-xorg-driver-voodoo x-server-xorg-driver-tdfx libglide3

also it seems in the "modlules" section make sure there is a "Load dri" and a "Load glx" line

see how it goes - good luck

---

### Post by Fidelio on 2007-03-16
OK. I'll try that. But how do I do it. I don't have permission to edit that file, and it says i am not the owner so I can't give myself permission.

---

### Post by glenndavy on 2007-03-16
probably easiest way is to open a terminal and do

sudo gedit /etc/X11/xorg.conf

to be honest im not sure what 'nice' editor ubuntu ships with by default, but i think gedit will be a safe bet.

---

### Post by glenndavy on 2007-03-16
probably easiest way is to open a terminal and do

sudo gedit /etc/X11/xorg.conf

to be honest im not sure what 'nice' editor ubuntu ships with by default, but i think gedit will be a safe bet.

---

### Post by Fidelio on 2007-03-16
Thanks
If I just replace vesa with tdfx in the xorg.conf file and reboot i get an 800x600 screen and even slower graphics.

Also did you mean literally open a reminal and type:

```
sudo apt-get install x-server-xorg-driver-voodoo x-server-xorg-driver-tdfx libglide3
```
I get a couldn't find package error.

---

### Post by Fidelio on 2007-03-16
Ok. I'm pretty sure the problem is that I have both onboard graphics and my voodoo 5 card. The installer detected the onboard and installed vesa drivers. 
Now I suppose the easiest thing would be to go into the bios and disable the onboard. But that doesn't appear to be available in my bios.
So I need to manually force the os to use the correct drivers.
Simply replacing 'vesa' with 'tdfx' in the xorg.conf file just doesn't work. It makes things worse. 
What other settings should I tweak?
The thing is, it's obviously using the voodoo card, because that's what's plugged in!

I've got the hang of editting system files and restoring them from backups now, so I don't feel like such an utter noob, but my lack of geek-hood is still evident.

---

### Post by glenndavy on 2007-03-16
> 
Also did you mean literally open a reminal and type...


yep... but instead perhaps try one at a time
```

sudo apt-get install libglide3
sudo apt-get install xserver-xorg-bla-driver

```
(etc)

its highly like these packages are already installed, but just trying to be sure

> 
Simply replacing 'vesa' with 'tdfx' in the xorg.conf file just doesn't work. It makes things worse. 
 What other settings should I tweak?


you checked this?
> 
also it seems in the "modlules" section make sure there is a "Load dri" and a "Load glx" line


dont know really  - like i said, i dont have a voodoo and never have had - im using what i've googled.

the way i read this;
[http://xorg.freedesktop.org/archive/X11R6.8.0/doc/tdfx.4.html](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/tdfx.4.html)
The defaults are already on and tdfx is the way to go

it also seems that xserver-xorg-driver-voodoo is concerned with voodoo2

so can you do 
```

dpkg -l|grep -i libglide3
dpkg -l|grep -i xlibmesa-dri
dpkg -l|grep -i x-server-xorg-driver-tdfx

```

and see if you get out put from each?

---

### Post by glenndavy on 2007-03-17
hey fidleo - 1000000 appologies... it was 4 in morning when i wrote that... when I said "x-server-xorg-driver-tdfx", i should have said "xserver-xorg-video-tdfx" 

at end of day however, dont think it will make a diff as it seems all those drivers are installed by default regardless

---

### Post by Fidelio on 2007-03-18
Thanks so much for all your help.
In the end I gave up. I'm going to try some other distributions. I'm currently running vector linux and looking at fedora and mandriva.
Vector installed very nicely and offered me a choice of graphics card drivers during setup, and runs tdfx properly.
I've also sort of realised that a lot of the things which are great about ubuntu are available in lots of other distributions. So It's Linux, yes, but Ubuntu, no.
cheers

---

### Post by glenndavy on 2007-03-18
hey best of luck - yeah - i do the rounds of distros every so often... enjoy the ride ;-)

---

