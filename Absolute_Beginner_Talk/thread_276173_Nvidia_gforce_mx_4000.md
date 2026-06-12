---
title: "Nvidia gforce mx 4000"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-10-12
Hi.
  JUst got the above graphics card but when i connect it Ubunto wont even load...it stops at various places during boot sequence.
Am i doing something wrong???

EDUT:ITs not "during" but just at the point prior to the logon screen comming up after the boot sequence has scrolled by

---

### Post by chuckyp on 2006-10-12
What do you mean by stopping?  Does X error out?

if so:

You can try switching to a vesa driver to fix some stuff if you need X.  You want to 
sudo nano /etc/X11/xorg.conf  and change the video driver line to vesa instead of nv or whatever your old card was.

The other option is just to install the nvidia drivers via nvidia.com or the ones in repos i.e.

sudo aptitude install nvidia-glx

---

### Post by xpod on 2006-10-12
Sorry m8..all i get is the usual boot scroll(all fine) then as it goes black when just about to show logon screen i get still a full black screen with nothing but a "-"
Not a blinking cursor and even if i try load the live cd it does the same just at the point the little logon tune plays...but no logon.

I`ll have a look back through what you said and see if i can use it....thanks btw...I prsently have onboard graphics via the "s3 savage" driver

EDUT:Theres a few "nvidia" bits in synaptic.....what would i need..glx..legacy???????
And should`nt the sys at least come on with the card plugged in.The bios has a "vga" or a "pci" setting and i chose pci as i assumed that was the correct choice....am i mabey wrong

---

### Post by xpod on 2006-10-12
Ive installed the nvidia stuff from synaptic and the pc seems to be booting ok now with the card installed but i cant find it listed or so dont even know if the machine is recognising it???

EDIT..My Xorg.config still says
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
        Driver          "savage"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "NEC CI A526"
        Option          "DPMS"
EndSection

I dont want to change things if the card aint even being recognised???

---

### Post by xpod on 2006-10-12
Right im now in the live cd..I got the card recognised and installed the drivers then run the reconfigure xorg.conf command and it went through the motions with the nvidia card as the subject but when i rebooted nothing...

I know a little about using backups but never from the live cd ....yet:D

---

### Post by wvslkr on 2006-10-12
You need to go into bios and disable the onboard card.  Then you should be able to use the new one.

---

### Post by xpod on 2006-10-12
I have done all that and the card was all recognised but ive messed up the "xorg.config" by running the commands given in the previous posts.

Just need to get an old one back and start again.The card and drivers are insatlled but just need configured....properly:D .If i try start normally just now i go to a box telling me about the xorg probs.

How do i use a back up from the live cd

---

### Post by xpod on 2006-10-12
Thats what the relevant part of the xorg.config  says from live cd
ction "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Driver		"vesa"
	BusID		"PCI:0:9:0"
EndSection

Section "Monitor"
	Identifier	"NEC CI A526"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"NEC CI A526"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

