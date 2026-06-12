---
title: "Setting 1280x800 Screen Resolution"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Mikey3883 on 2007-02-09
Hi,

I've just installed ubuntu onto my laptop, but it will only let me set my resolution to 1024x768. Ive got a 15.1" widescreen that i run at 1280x800 in Windows. I have an Intel Mobile 915GM/GMS/910GML Express integrated graphics card (if that makes much of a difference).

Could somebody give me some guidance on how to get it to the resolution i want? I can handle my way around the terminal but am still relatively new to linux and its many many commands etc, so dont be afraid of being too patronising....

Thanks in advanced :)

---

### Post by housam on 2007-02-09
You can edit your resolution

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by PartisanEntity on 2007-02-09
You have to edit your xorg.conf file.

The way I do it is to open up the terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

Then look for: **Section "Screen**"

And add your screen resolution to each line in the same way the existing resolutions have been typed. Save and close.

Here is my Section "Screen":

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40M? [GeForce Go 6200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

You should then be able to choose the screen resolution you like through: System > Preferences > Screen resolution (You may have to restart the x server first by doing CTRL + ALT BACKSPACE)

---

### Post by Mikey3883 on 2007-02-09
Hey Partisan,

Thanks for the reply, i opened the xorg.conf file and found that "1280x800" was the only resolution listed... i added the others in the vain hope that it might do something (which it didnt)... i restarted X but the 1280x800 option still isnt listed in the screen resolution preferences. Heres the Screen section of my xorg.conf file incase ive made some kind of mistake...

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800""1024x768""800x600""640x480"
	EndSubSection
EndSection
```

---

### Post by chameleonkid on 2007-02-09
It's kind of funny because I just had this problem when I installed this on my laptop as well. What worked for me was making sure I had the right drivers. I have an ait card which I thought would work with the ati driver but no. I had to swtich my driver to fglrx. Make sure you have the right drivers installed.

---

### Post by housam on 2007-02-09
As I mentioned in my previous post , open your xserver-xorg and press enter for every thing ( leave every thing as it is ) till you get the sitting page as in the attachment and select  1280x800 ( by pressing space )  and continue to go out.

---

### Post by Mikey3883 on 2007-02-09
I've tried reconfiguring my xserver using the config utility and it didnt work...

Driver wisde i've had a look around and i cant seem to find anything for Xfree86 (which is what ubuntu uses?), and even if i could find some i have no idea how to install them....

There is something i found called 915Resolution which is a hack (for my graphics card) to get it to display the correct resolution in linux but i wouldn't know where to begin using it or automatically using it at each boot up... the site can be found at [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Anybody willing to give some advice?

---

### Post by PartisanEntity on 2007-02-10
Unfortunately I cannot give you any more advice, I have tried both the method I mentioned as well as the method mentioned by housam and they have both always worked for me.

---

### Post by meborc on 2007-02-10
this is really strange... as X should use the resolution in the conf file... you could take a look at this [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) but i guess it only has the suggestions already mentioned here...

just make sure that you edited the right conf file and not a backup one... ahh... i can't think of anything else :(

---

### Post by PartisanEntity on 2007-02-10
That's a good point, make sure you typed: sudo gedit /etc/X11/xorg.conf

---

### Post by Mikey3883 on 2007-02-10
i definately typed: sudo gedit /etc/X11/xorg.conf, it the asks for the admin password, which i give it and then it opens in gedit. After running the config utility my xorg.conf now looks like this (and still runs in 1024x768 )...

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
```

---

### Post by The Seeker on 2007-02-10
[This thread](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution) should help.

---

