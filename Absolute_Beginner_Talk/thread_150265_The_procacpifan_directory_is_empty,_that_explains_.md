---
title: "The /proc/acpi/fan directory is empty, that explains why my fan is so loud..."
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-25
The /proc/acpi/fan directory is empty, that explains why my fan is so loud...

So that means that my fan is not detected with acpid. The acpid daemon is running:

$ ps -ef|grep acpid
root        12     9  0 14:22 ?        00:00:00 [kacpid]
root      8401     1  0 14:22 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket

So I've been trying to figure out how to control my two fans (system and cpu), there is a lot of information, but it seems like there is not a clear cut answer.

I'm running on:

MSI MS-7184 motherboard.
AMD Athlon 64 X2 3800+ processor.
Northbridge: ATI RS482 and Southbridge: ATI SB400 chipset.
1 GB Ramm

Guidance or information on how I can get my two fans recognized would be greatly appreciated.

Thanks,

---

### Post by Pragmatist on 2006-03-26
If it were me, I'd play around with the several related packages in synaptic:
[B]lm-sensors
mbmon
xmbmon
sensord
xsensors[/B]
And, if you use KDE, **ksensors** (a front-end to lm-sensors)

I found them all by doing a search in synaptic using keyword: **fan**
Unfortunately that gives a somewhat large list (includes phrases like 'fancy' etc..) However, if you use the keyword 'fan' you'll be able to scroll and read a blurb about each of the above packages.

---

### Post by jtp51 on 2006-03-26
Thank you.

sensord was the only one available...

$ sudo apt-get install sensord
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  librrd2 ttf-dejavu
The following NEW packages will be installed:
  librrd2 sensord ttf-dejavu
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1091kB of archives.
After unpacking 2454kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main ttf-dejavu 1.11-1 [804kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main librrd2 1.2.11-0.3 [230kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main sensord 1:2.9.1-4ubuntu3 [56.2kB]Fetched 1091kB in 2s (408kB/s)

Preconfiguring packages ...
Selecting previously deselected package ttf-dejavu.
(Reading database ... 87176 files and directories currently installed.)
Unpacking ttf-dejavu (from .../ttf-dejavu_1.11-1_all.deb) ...
Selecting previously deselected package librrd2.
Unpacking librrd2 (from .../librrd2_1.2.11-0.3_i386.deb) ...
Selecting previously deselected package sensord.
Unpacking sensord (from .../sensord_1%3a2.9.1-4ubuntu3_i386.deb) ...
Setting up ttf-dejavu (1.11-1) ...

Setting up librrd2 (1.2.11-0.3) ...

Setting up sensord (2.9.1-4ubuntu3) ...
Starting sensor daemon: sensord.

---

### Post by jtp51 on 2006-04-04
I am still unable to get lm-sensors to work.

I need to back up at this point - what populates the /proc/acpi/fan directory?

(That is most likely the true problem.)

Thanks,

---

### Post by Pragmatist on 2006-04-04
Unfortunately I recently uninstalled ACPI, and I don't remember what I saw in /proc/acpi/fan the last time I was helping you (there were entries though).

Now that I re-read your OP, I'm skeptical that ACPI can control how loud your fan is. Are you sure of that? If not, there are kits you can buy that minimize the sound. However, you'll probably get better results with a new, quiet, fan. Then there is always the possibility that the fan is brushing up against something, or the case hasn't snapped closed completely.

---

### Post by jtp51 on 2006-04-05
Pragmatist: Thank you.

I'm at the point to look for a hardware solution. You're right, I don't know if acpi is the issue.

Basically, I believe that the newer ATI chipsets are not supported yet.

This belief is based on the fact that in Windows, the fan runs quietly, but booting into Ubuntu, the fan is a lot louder than Windows use.

Thanks,

---

### Post by mlind on 2006-04-05
I guess /proc/acpi/fan directory is only populated when you have sensors daemon
installed and you've detected your fans using sensors-detect. 
sensors-detect will load correct modules for the kernel.

---

### Post by moe_syzlak on 2007-11-27
change the "AIGLX" to "on" and it will stop the crazy fan noise after about 10mins after u restart X server. the solution to this problem is in your xorg.conf:

# Xorg configuration created by livna-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "Xinerama" "0"
EndSection

Section	"Module"
#	Load "GLcore"
#	Load	"vbe"
	Load "dbe"
Endsection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us+inet"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "LPL"
	HorizSync    30.0 - 75.0
	VertRefresh  60.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "GeForce Go 7300"
	Option	    "Accel" "true"
	Option	    "AddARGBGLXVisuals" "True"
	Option	"NoLogo"	"True"
	Option	"DRI"	"true"
	Option	"XAANoOffscreenPixmaps"	"true"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "RenderAccel" "true"
	Option	    "TwinView" "0"
	Option	    "metamodes" "1440x900 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

---

