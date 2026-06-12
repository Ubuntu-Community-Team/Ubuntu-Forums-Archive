---
title: "Setting a Wide Screen Resolution"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by SamsLembas on 2007-01-20
I have just installed Ubuntu on my PowerPC, 17" iMac, and have been unable to figure out how to make Ubuntu use a wide screen resolution. When I open Screen Resolution Preferences, the options are 1024x768, 800x600, and 640x480. When one of these is selected, the image is stretched to fit the screen. Any ideas of how I can fix this?




Thanks for the help,
SamsLembas

---

### Post by ctt1wbw on 2007-01-20
You will have to edit your xorg.conf file.  Maybe someone a bit more advanced than me can help you, but it's something like this:

First you need to make a backup of your xorg.conf file.

mv /etc/X11/xorg.conf /etc/X11/xorg.conf_back

Then:

sudo gedit /etc/X11/xorg.conf

Look for the section listing your screen resolutions and replace them all with yours, probably 1440 x 900.  Save the file and reboot and that should be all there is to it.

---

### Post by SamsLembas on 2007-01-20
I went through the file and replaced all 1024x768s with 1440 x 900. When I restarted, the situation was the same, only using 1024x768 was not an option.

Here is the section of my xorg.conf file that seems to relate to video. This is the original, unedited version.



Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Buck2348 on 2007-01-20
I have often seen the following command recommended to adjust resolution:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I believe it takes you through a fairly lengthy dialog.  They say to just accept the defaults if you don't know what to choose in a dialog page.  There is also a software package called "915resolution" which works with Intel graphics cards--it's in the repos.

Buck

---

### Post by SamsLembas on 2007-01-20
I tried doing that, but it gave me the following error durring the secound step of the dialog:

xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070120190833


The file is not customized. However, I did customize it and then revert it back to the backup (see my post ubove), so I guess that is making it think the file is customized. Is there any way to make it keep going anyways/make it stop thinking it was customized? It was asking me for screen resolutions while it was running, which was very encouraging.

---

### Post by Buck2348 on 2007-01-20
I'm afraid I can't tell you any more--/etc/X11/X is just a link to an executable file so it's hard to see how you could customize it.  The reference to xorg.conf doesn't sound like a fatal error, so I don't know what's going on.

We need some expert advice, please!

Buck

---

### Post by Andrew Panin on 2007-01-20
I had the same problem for my wide-screen laptop and desktop PC. On the first one I did everything simple:

1. Start console and type "sudo nano /etc/apt/sources.list". You'll be prompted for the root password. It's the same that you log into system.

2. In open NANO editor find the lines about "universe" repository (two adjacent lines, I don't remember exactly) and uncomment them (remove "#" from the beginning of each line).

3. Press Ctrl+O, then confirm saving.

4. After that you should either run "sudo apt-get update", then "sudo apt-get install 915resolution"; or you can start your favourite packages manager (i. e. Adept in KDE, Kubuntu). Also, you can "sudo aptitude" instead. Then, update packages list, find and select that 915resolution package.

I've also tried to set up 915resolution manually, it's not that diffucult as it seems. Just find a standalone package via Google, then unpack it and read a short manual with installation example.

For my desktop that uses 1280x1024 I edited /etc/X11/xorg.conf manually. Everything worked great, but don't forget to make copy before any actions (being in /etc/X11, type "sudo cp xorg.conf xorg.conf.old") The structure of the file doesn't look complicated. I read the "man" pages for it in addition.

Hope, this will help a bit. :-)

---

### Post by SamsLembas on 2007-01-21
Isn't 915resolution only for Intel graphics cards?


I tried reinstalling the OS in attempt to make the previously posted command work, but it still gives me that error.

---

### Post by jbonll05 on 2007-01-21
From another "Noobie"
  Do you have the NVidia driver install from the repos? It has helped me with resolutions.
JB

---

### Post by SamsLembas on 2007-01-21
To the best of my knowledge, there are no nVIDIA drivers for PPC Linux :(

---

### Post by SamsLembas on 2007-01-21
I just restarted my system to find that the bottom of my screen was cut off, and it was still stretched out as usual. When Iowered the screen resolution, all of my desktop came into view, but there was also a large gray area bellow the bar at the bottom of my Gnome desktop. A quick look at my xorg.conf showed me that running "sudo dpkg-reconfigure -phigh xserver-xorg" had changed my xorg.conf before crashing (I noticed that it had changed my "device" from NVIDIA Corporation NV34M [GeForce FX Go5200]" to "Generic Video Card", but it may have done more) . I reverted to the backup that it had made and am now back at the state I was at the beginning of this thread.

I do not know if any of this is relevant or not.

---

### Post by SamsLembas on 2007-01-21
I messed up my xorg.conf file, and now when I try to boot I just get a blank screen at the time when I should get the login screen. Is there a way I can boot into a command line mode so I can revert to my backup xorg.conf file?

---

### Post by 454redhawk on 2007-01-21
> **SamsLembas said:**
> I messed up my xorg.conf file, and now when I try to boot I just get a blank screen at the time when I should get the login screen. Is there a way I can boot into a command line mode so I can revert to my backup xorg.conf file?


Hit the ESC key prior to boot (hit several times if required) then choose the recovery mode.

---

### Post by BCRailrodder on 2007-01-21
You can get to another terminal by using ctl-alt-f1 (you could use f1 thru to f6 (I think) ) and a new command line will come up.  Log back in and use the same command as before to access xorg.conf.

You can then reboot by issuing a "sudo reboot" command.

Good Luck,

Kent

---

### Post by SamsLembas on 2007-01-22
I got the ctl-alt-f1 thing to work, and I can now boot normaly. Thank for the help.

I am now back in the original situation, which is still not very good. The picture is stretched to fit my wide screen PowerPC iMac, and when I run "sudo dpkg-reconfigure -phigh xserver-xorg" I get the following error:

xserver-xorg postinst warning: not updating /etc/X11/X; file has been
customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20070120190833


Does anyone know what is going on? As I said before, I just installed this system when I first ran that command, so nothing is customized.

---

### Post by tomBorgia on 2007-01-22
"I went through the file and replaced all 1024x768s with 1440 x 900. When I restarted, the situation was the same, only using 1024x768 was not an option." - this bits fine, as long as the "Depth 24" bit looked like this -

Depth 24
Modes "1440x900" "800x600" "640x480"
EndSubSection
EndSection

You'd need to make sure that this bit - 

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Reflects the values for horizontal sync and vertical refresh of your monior (look it up in the manual / google). 

Worked for me when changing to a flatscreen monitor, didn't need to update anything... but then that wasn't on a mac!

Tom.

---

### Post by SamsLembas on 2007-01-22
Don't LCD monitors not have horizontal syncs/vertical refreshes?

I guess I should try taking them out when I have time (assuming I am right), but I don't have time right now and I doubt it will help.

---

### Post by SamsLembas on 2007-01-22
I just tried taking those lines out, but it did not work.

I am still trying to get the info on my monitor, but it does not seem very likely to help to me. Finding a way to get "sudo dpkg-reconfigure -phigh xserver-xorg" to work seems more likely to help. Does anyone have any idea what is going on with the error I have been getting there?

---

### Post by caltabellotta on 2007-01-22
hey all...im having the same problem on a hp laptop, getting almost the same results as sam..just errors showing that when i try to change the resolution, lines cannot be read after updating.](*,) 
stuck at 1280x760 on a 1200x800 monitor, could not get the 915resolution due to some code errors...this in turn is not allowing me to go any farther

thanks

---

### Post by tomBorgia on 2007-01-23
> **SamsLembas said:**
> Don't LCD monitors not have horizontal syncs/vertical refreshes?

I guess I should try taking them out when I have time (assuming I am right), but I don't have time right now and I doubt it will help.

Hmm, seems your right - Funny cuz there seemed to be figures available for my montior! Anyway I guess i must have just been lucky because all I needed to do was edit the xorg.conf file. What errors are you getting now?

---

### Post by SamsLembas on 2007-01-23
Is there any chance that using a different Linux distribution would fix this? There does not seem to be any solution, and Ubuntu is completely useless with the display like this.

---

