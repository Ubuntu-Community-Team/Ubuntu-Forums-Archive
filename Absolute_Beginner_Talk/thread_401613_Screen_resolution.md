---
title: "Screen resolution"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by yoramdavid on 2007-04-04
Hello, I have the following:
Motherboard:
Asus A7N8X Deluxe (5 PCI, 1 AGP Pro, 3 DIMM, Audio, Dual LAN, IEEE-1394)
Motherboard Chipset:
nVIDIA nForce2 SPP
Graphic card:
NVIDIA GeForce FX 5700LE (Microsoft Corporation) (256 MB)

Problem:
I have a maximum resolution of 1024x768@61Hz which I cannot change.

Steps I tried to fix the problem:
Edit the Xorg.conf manually (sudo gedit /etc/X11/xorg.conf) or the Xserver.conf graphically (sudo dpkg-reconfigure xserver-xorg)
Each time I edith either of these, I get a funny screen with xserver error not being able to boot due to graphical errors...

Also:
Install Nvidia Drivers:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Install Nvidia driver in Ubuntu - The Default

Insert the following lines into the new file
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
-----------------------------------------------------------
Open the terminal and write:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable (sudo nvidia-xconfig if using dapper)
sudo modprobe nvidia dmesg

In the left window of the menu editor choose System Tools, then click the New Entry button.
Entry Editor Name: Nvidia Settings
Comment: <What ever you like>
Command: nvidia-settings
Icon: <Pick a icon for it or just leave it>

I also did what I found on these threats:
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
[http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)

Can anyone help, please?
Yoram<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by brentoboy on 2007-04-04
ok, try this out
```

sudo apt-get remove nvidia-settings
sudo apt-get install nvidia-glx

```

I noticed some time ago that nvidia-settings "conflicts" with nvidia-glx -- meaning, if you add one of them, it removes the other.

so, get nvidia-glx in there, and then hand edit the xorg.conf file like so

```
sudo gedit /etc/X11/xorg.conf
```

find the section like this...
```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6200]"
    Driver         "nvidia"
EndSection

```
your driver is probably either vesa or nv  change it to nvidia like the example above.

then, restart your gui
(easiest done by pressing ctrl + alt + f1 and then logging in and running:  sudo /etc/init.d/gdm restart)

if glxgears runs (from a terminal) you have the nvidia driver in place.

---

### Post by j002 on 2007-04-04
I think the problem is it won't recognise your monitor.

---

### Post by oilchangeguy on 2007-04-04
j002, have you got your hard drive issue resolved yet? if not please stick with that. it's not a monitor problem it's a graphics card driver problem. and this is the main reason i run a 14 inch crt with my ubuntu box. and leave the 19 inch acer widescreen, and the nvidia g6200 to the box with xp pro. i like the 1440x900 resolution and no problems to get it.

---

### Post by yoramdavid on 2007-04-05
Thank you for your help.
Uninstalling and reinstalling the above driver did not change anything.
And adding the "NVIDIA Corporation NV43 [GeForce 6200]" make the xserver not responding like whenever I do any change on the xorg.conf. I had to restore the backup to be able to log on again in graphical mode.
My Section "Device" in my xorg.conf file looks like this:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:3:0:0"
EndSection

These settings were input either when Installed the nvidia drivers yeterday (at some point I had the nvidia logo appearing when I did one of the things I found on some threat-cannot remember which, already did so many...)

The xorg.conf looks something like this (I cut the irrelevant parts):
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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

whenever I change the hsync or vsync or ada a mode in the display resolutions, the system cannot boot.

Any other ideas? Is my monitor not recognizes?
Thank you.
Yoram

---

### Post by Jovec on 2007-04-05
> **yoramdavid said:**
> Thank you for your help.
Uninstalling and reinstalling the above driver did not change anything.
And adding the "NVIDIA Corporation NV43 [GeForce 6200]" make the xserver not responding like whenever I do any change on the xorg.conf. I had to restore the backup to be able to log on again in graphical mode.
My Section "Device" in my xorg.conf file looks like this:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:3:0:0"
EndSection



The Identifier must match up throughout your xorg.conf.  If you changed the Identifier to ""NVIDIA Corporation NV43 [GeForce 6200]", you'll notice in the Screen section the Device it is trying to use is still "Generic Video Card."  For the most part, you don't need to change the identifier.

However, the Driver "vesa" line should really read Driver "nv" or Driver "nvidia"

The nv driver is the included xorg Nvidia driver that will work better than vesa for your card.  The nvidia is the proprietary Nvidia driver that will work best with your card, but you must install this separately.


> These settings were input either when Installed the nvidia drivers yeterday (at some point I had the nvidia logo appearing when I did one of the things I found on some threat-cannot remember which, already did so many...)

The xorg.conf looks something like this (I cut the irrelevant parts):
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
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

whenever I change the hsync or vsync or ada a mode in the display resolutions, the system cannot boot.

Any other ideas? Is my monitor not recognizes?
Thank you.
Yoram

You'll also need to define higher resolution modes, but of course you'll have to work within the confines of what your monitor (and video card) can display.  The manual or online specs for your monitor should have the proper H/V timings.  If you give the make/model of your monitor I'll try to find those for you.

---

### Post by yoramdavid on 2007-04-05
Hello,

Thank  you for your help.
I have tried several times to change the resolution and the vertical and horizontal refresh rates.
Each time xserver could not start.
But I am willing to try again.
My motherboard, Video board and monitor are as follows:
Motherboard:
CPU Type  	AMD Athlon XP-A, 2079 MHz (6.25 x 333) 2800+
Motherboard Name  	Asus A7N8X Deluxe (5 PCI, 1 AGP Pro, 3 DIMM, Audio, Dual LAN, IEEE-1394)
Motherboard Chipset  	nVIDIA nForce2 SPP
System Memory  	2048 MB (DDR SDRAM)
BIOS Type  	Award (11/12/04)
 
Display:
Video Adapter  	NVIDIA GeForce FX 5700LE (Microsoft Corporation) (256 MB)
3D Accelerator  	nVIDIA NV36

Yoram
Monitor  	ViewSonic P95f

Let me know if you need more details and I'll try to find them.

---

### Post by kyphi on 2007-04-05
In a terminal, type

sudo dpkg-reconfigure -phigh xserver-xorg

Using your up/down keys scroll to the resolution you want, press the spacebar to select, then enter to exit.  Note the space before -phigh.

You then need to log out and then back in.

---

### Post by yoramdavid on 2007-04-05
Hello,
Thank you for your help.
The good knew is that I get the resolution I want now. thank you very much for that!! I am already very happy!
The bad news is that the refresh rate is still at 60Hz. I can go up to 85 at 1280x1024.

I had already run this command before and answer the questions to my best, but for most of them I did not know the answer. But the resolution steps I never succeeded because i did not know how to check the boxes (I swear I tried all the keys of the keyboard but the spacebar!) excuse my stupidity.
At the beginning it asked for the video card:vesa, nv, etc. I put nv.
The times I did this before there were much more steps than this time: after entering the resolutions I wanted, the application closed.

yoram

---

### Post by Jovec on 2007-04-05
> **yoramdavid said:**
> 
Monitor  	ViewSonic P95f

Let me know if you need more details and I'll try to find them.

Your HorizSync should be 30-110
Your VertRefresh should be 50-160

---

### Post by kyphi on 2007-04-05
Hello Yoram,

I gather that you have a CRT monitor that would make a 60 Hz refresh rate rather painful on the eyes.

Reading through your posts I wonder if  you actually have the nvidia driver installed.  Did you, after downloading nvidia-glx, go to the terminal and type in

sudo nvidia-glx-config enable

Did you use Automatix or Easy Ubuntu to get the nvidia drivers ?

Cheers,
Kyphi

---

### Post by yoramdavid on 2007-04-06
Hi,
Thank you for your help.

I run the "sudo apt-get install nvidia-glx" command and got the following comments:

Os seguintes pacotes foram instalados automáticamente e já não são necessários:
  python-at-spi libmono-sharpzip0.6-cil libkonq4 libwv-1.2-1 beagle
  libmono-system-runtime1.0-cil phalanx libassa3.4-0 libgsf0.0-cil
Utilize 'apt-get autoremove' para os remover.
Pacotes sugeridos :
  nvidia-kernel-source
Os seguintes NOVOS pacotes serão instalados:
  nvidia-glx
0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário fazer o download de 4066kB de arquivos.
Depois de descompactar, 12,6MB adicionais de espaço em disco serão utilizados.
Obter:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted nvidia-glx 1.0.8776+2.6.17.7-11.2 [4066kB]
Obtidos 4066kB em 20s (198kB/s)                                                
A seleccionar pacote anteriormente não seleccionado nvidia-glx
(Lendo a base de dados ... 154034 ficheiros e directórios actualmente instalados.)
A descompactar nvidia-glx (desde .../nvidia-glx_1.0.8776+2.6.17.7-11.2_i386.deb) ...
A instalar nvidia-glx (1.0.8776+2.6.17.7-11.2) ...

Do I need to run the 'apt-get autoremove' command to remove unnecessary packs?
(  python-at-spi libmono-sharpzip0.6-cil libkonq4 libwv-1.2-1 beagle
  libmono-system-runtime1.0-cil phalanx libassa3.4-0 libgsf0.0-cil)

Then ran the "yo@yo-I:~$ sudo nvidia-glx-config enable" command, restarted the Xsever. I got to the black and white screen and I did not know how to restore the X in graphic mode, so I typed sudo reboot.
When it rebooted, I got the nvidia logo displayed on the screen and was able to logon normally but still cannot change the screen refresh rate.

Yoram

---

### Post by Jovec on 2007-04-06
> I did not know how to restore the X in graphic mode

Press Ctrl+Alt+Backspace, or sudo /etc/init.d/gdm restart (substitute kdm or xdm if that is your login manager)


You're close!

Edit your xorg.conf and do the following:

Change the following in the Monitor section to read

```
HorizSync 30 - 110
VertRefresh 50 - 160
```

*I looked these up for your Monitor model*

Now, add the following modes to the 24 bit depth section under Screen (you can delete all the non-24 bit depth modes if you wish).  You shouldn't have to change any Identifier or Device name, just leave those at whatever they currently are.

```
Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1600x1200" 1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```

You can add other video modes if you choose.

Reboot/Restart X server

---

### Post by yoramdavid on 2007-04-06
Victory!!
Thank you very much for the precious help of you all.
I am now on a 1600x1200@85hz in a 24 depth  mode.
What I do not understand is that I already tried these frequencies before (got them from ViwSonic site for the p95f+ but they did not work. It seem the drivers were better installed now, as they appear on the xorg.con file.
Thanks again.

Yoram:)

---

