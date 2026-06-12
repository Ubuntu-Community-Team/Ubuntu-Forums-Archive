---
title: "Installation Problem"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by Williams477 on 2005-07-08
After a few weeks of trial and error and I finally got the computer to read the Ubuntu boot CD before loading windows. The main screen comes up and asks me to either type 'server' or just press enter for the default install. I pressed enter and the screen went black then white lettering came up. It says it's loading the kernel but then the computer just restarts and goes through it's boot up process again. What's going on?

---

### Post by codejunkie on 2005-07-08
it's an acpi problem try these commands at the boot prompt and let me know how it works for you.
```
linux acpi=off
``` for the install disk
```
live acpi=off
``` for the live cd

---

### Post by Williams477 on 2005-07-08
Thanks, that worked. But now I can't get Ubuntu to load. I choose to use the Ubuntu Operating System then a long list of commands come up and it acts like it's going to load. Then it gets to something that says loading hot plug subsystem or something like that and it just stops working and I have to turn the pc off.

---

### Post by Williams477 on 2005-07-08
I've been going through the forums to try to figure out what I can do to fix it. Apparently the hotplug subsystem has something to do with gathering the information on your extra devices. Some of the other posts suggested that I go into bios and turn off the usb controls, so I did that and it still didn't work. Then I tried simply unplugging the usb cords I had connected to the computer and that didn't work. I also read that you could press ctrl-c to skip something, so I tried but that didn't work but then I noticed that my keyboard wouldn't do anything and I couldn't turn on Number Lock. So I'm thinking it may have something to do with my keyboard.

---

### Post by codejunkie on 2005-07-08
[QUOTE=Williams477]Thanks, that worked. But now I can't get Ubuntu to load. I choose to use the Ubuntu Operating System then a long list of commands come up and it acts like it's going to load. Then it gets to something that says loading hot plug subsystem or something like that and it just stops working and I have to turn the PC off.[/QUOTE]
i don't know if this will help you or not but i had that problem on my compaq also the thing that was causing it was i had an add on video card/ati-radeon9200 pci card installed and compaq locked my motherboard where i couldn't disable the onboard video and when i removed the video card the ati 9200 and just used the onboard video it worked great. so if your using an add on video card in your computer and your motherboard has onboard video try going into the bios and make sure onboard video is disabled this might the problem hope this helps and let me know if this works for you.

---

### Post by Williams477 on 2005-07-08
Thanks that worked, sort of. I had to enable the onboard device and disable the PCI card to get Ubuntu to load. Now I have yet another problem. It's loaded but the screen resolution is absolutely terrible. I went into the Screen Resolution to fix the problem but the only one there is to select is 640 x 480. What can I do to fix this? And is there a way I can get Ubuntu to work with my PCI card? That way I don't have to keep changing the BIOS if I want to load Windows instead of Ubuntu.

My PCI card is a Nvidia GeForce 4000

---

### Post by Williams477 on 2005-07-08
My xorg.conf is as followed:

> Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"v70s"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"v70s"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

---

### Post by poofyhairguy on 2005-07-09
[QUOTE=Williams477]Thanks that worked, sort of. I had to enable the onboard device and disable the PCI card to get Ubuntu to load. Now I have yet another problem. It's loaded but the screen resolution is absolutely terrible. I went into the Screen Resolution to fix the problem but the only one there is to select is 640 x 480. What can I do to fix this? [/QUOTE]

This command:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by codejunkie on 2005-07-09
[QUOTE=Williams477]Thanks that worked, sort of. I had to enable the onboard device and disable the PCI card to get Ubuntu to load. Now I have yet another problem. It's loaded but the screen resolution is absolutely terrible. I went into the Screen Resolution to fix the problem but the only one there is to select is 640 x 480. What can I do to fix this? And is there a way I can get Ubuntu to work with my PCI card? That way I don't have to keep changing the BIOS if I want to load Windows instead of Ubuntu.

My PCI card is a Nvidia GeForce 4000[/QUOTE]
i don't know if this will work on your computer but you could always switch back if it doesn't i have read about some people having issues with the"i810" driver so you could try using the vesa driver but i think this might disable 3D acceleration but i don't seem to have any problems with mine using the vesa driver and i play some games like super tux and the basic games included with gnome so i don't know about the games that require 3d acceleration you can change to the vesa driver like this```
sudo gedit /etc/X11/xorg.conf
```find this section 
```
 
Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver [COLOR=Blue]"i810"[/COLOR]
BusID "PCI:0:2:0"
EndSection
```
and replace "i810" with [COLOR=Blue]"vesa"[/COLOR] save and restart the computer that should fix the resolution problem but i can't guarantee anything though.

and about fixing it to where it only uses the pci card  i found a solution on here once that involved setting up the onboard video and the pci card as a dual head setup so you could use just the pci card and not use the onboard video that worked so i'll try digging through some of my old bookmarks and find that for you but could you give me a little more info on your computer like 
manufacture 
model number
monitor model
but if you or someone else built the computer just the motherboard model number
and the montior model.
and if the computer was made by a company like compaq, gateway, or dell etc does the computer have an agp slot and if does is it disabled.

---

### Post by Williams477 on 2005-07-09
Oh a million thank you's! That fixed the problem.

As for the system information:

HP Pavilion a1006n
780 MB RAM
100 GB Hard Drive (Windows)
60 GB Hard Drive(Ubuntu)
HP Pavilion v70s Monitor
No AGP Slot
Nvidia GeForce Mx4000(I think, it's something 4000).
2 Internal CD Drives, 1 external
No Floppy Drive
Westell WireSpeed DSL Modem
HP DeskJet 3845 Printer

---

### Post by codejunkie on 2005-07-09
[QUOTE=Williams477]Oh a million thank you's! That fixed the problem.

As for the system information:

HP Pavilion a1006n
780 MB RAM
100 GB Hard Drive (Windows)
60 GB Hard Drive(Ubuntu)
HP Pavilion v70s Monitor
No AGP Slot
Nvidia GeForce Mx4000(I think, it's something 4000).
2 Internal CD Drives, 1 external
No Floppy Drive
Westell WireSpeed DSL Modem
HP DeskJet 3845 Printer[/QUOTE]
i kinda had a guess that is was a compaq/hp computer they seem to like disabling the agp slot and the option to disable onboard video on there computers for some reason. so the only way to use the pc card you have is to use the dual head setup  im still looking for the info on how to do it as soon as i find it i'll post the link here but i've got tons of bookmarks to look through so it might take me a day or so but i'll try my best to find it.

---

### Post by Williams477 on 2005-07-09
Thanks again for the help.

I got the macromedia flash plugin to finally go in for FireFox but now i'm running into another problem. I don't get any sound. I searched the forums and found limited information on it.

I installed the plugin by extracting it to my desktop then going through the terminal and navigating to the install file's location.

Then I updated my FireFox version by going to their site, downloading it, and just running the install file by double clicking.

---

### Post by codejunkie on 2005-07-10
[QUOTE=Williams477]Thanks again for the help.

I got the macromedia flash plugin to finally go in for FireFox but now I'm running into another problem. I don't get any sound. I searched the forums and found limited information on it.

I installed the plugin by extracting it to my desktop then going through the terminal and navigating to the install file's location.

Then I updated my FireFox version by going to their site, downloading it, and just running the install file by double clicking.[/QUOTE]
if you have sound in ubuntu like playing music etc but no sound through the flash plugin try this guide this is how i got it to work [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) if you have no sound at all i don't really know because there are so many sound cards out there it's hard for me to remember how t set each of them up.

---

