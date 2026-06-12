---
title: "[SOLVED] Install Restricted Driver, won't boot in GUI"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Pharisee on 2007-09-02
So basically now that I have got another NIC I am not experiencing anymore Internet issues. However now after installing my OS I update the driver from the Restricted Drivers menu, I restart and then XServer basically dies upon reboot.

The first time it happened I thought perhaps I did something wrong because I was downloading other updates as well and that may of caused some conflict. The second time I did it, I only installed the driver and it did the same thing. 

I seriously do not want to do it a third time and see it happen again. Can anyone think of why it is causing XServer to die?

My system specs are:

Intel Core 2 Duo E6600 (2.4GHz)
GA-965P-DQ6
2GB DDR2 800MHz Cosair RAM
NVIDIA 8800GTS 320MB
320GB Segate
2x SATA DVD Writers

Thanks a lot!

---

### Post by Pharisee on 2007-09-02
Okay, while waiting for a reply I have browsed the forums and Google looking at different guides seeing if I am missing something. I tried a guide I found linked from here and that didn't work either. 

This time I wrote down the 2 errors I noticed in the Xorg message. I didn't write down the exact words but it basically said:

(EE) Failed to load module "wfb" doesn't exit
(EE)NVIDIA(0): tried(?) libwfb but ScreenInit not found

Thanks everyone!

---

### Post by Pharisee on 2007-09-02
I managed to figure this out myself :)

After searching the forums and trying several different methods, I came across [this]("http://ubuntuforums.org/showpost.php?p=2687793&postcount=17") thread and the method worked for me.

Since I had already reinstalled my system for the 6th or 7th time, I was not in the same situation as the entry so I went about it slightly different.

1. I opened up the terminal 

**Applications --> Accessories -> Terminal**

2. I then typed:

```
sudo apt-get install nvidia-glx-new
```

3. After that I downloaded the driver from the NVIDIA site [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run").

*I have however uploaded the file you need to my website [here]("http://alen.id.au/libwfb.so"). After downloading it copy it to the same directory listed in the steps (**/usr/lib/xorg/modules/***)

4. I extracted the module (replace the file name with the appropriate driver for your card):

```
 sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1 -x
```

5. I then copied the file to where it was needed:

```
cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules/libwfb.so 
```

6. I then deleted the extracted files and restarted.

7. I noticed in my Restricted Drivers Manager that my device was still showing as disabled so I went into my xorg.conf file and edited the settings:
```

cd /etc/X11
sudo gedit xorg.conf
```

Th Device section looked like this:

```
Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
```

I changed it to the following:

```

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8800 GTS]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection
```

I changed the Driver from "nv" to "nvidia" and then I restarted.

8. Also for some reason my native resolution wasn't picked up (16:10 ratio) I added it manually to the xorg.conf file by doing this:

```
cd /etc/X11/
sudo gedit xorg.conf
```

When the file opened up I had the following code:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
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
```

I then manually add my native resolution (1680x1050):

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I then saved the file and restarted.

Then I started writing up this entry :P Everything is working now, and I hope it stays that way :P I decided retype the advice in the other post just in case someone was in a similar position to me, including the issue with the screen resolution

Take care!

---

