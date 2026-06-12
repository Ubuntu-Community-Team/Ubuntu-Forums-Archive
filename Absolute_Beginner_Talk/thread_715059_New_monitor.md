---
title: "New monitor"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2008-03-04
Ok  I just bought a HP w1907 LCD and have this odd oblong look to my screen,is there any way to update this or just reload nvidia 5500:confused: drivers?

---

### Post by skymera on 2008-03-04
can you set the correct resolution in nvidia-settings?

---

### Post by J11Gyro on 2008-03-04
No I tried that it needs to be like 1150x720 like in windblows but there are no resolutions like that in the nvidia settings

---

### Post by J11Gyro on 2008-03-04
Is there any way I can force a resolution by editing the xorg file?

---

### Post by stchman on 2008-03-04
> **J11Gyro said:**
> Ok  I just bought a HP w1907 LCD and have this odd oblong look to my screen,is there any way to update this or just reload nvidia 5500:confused: drivers?

Add "1440x900" in the line of resolutions in your /etc/X11/xorg.conf file.  Make sure it is the first and don't forget the quotes.  Restart the workspace CTRL-ALT-BKSP and all will be good.

You will have to sudo gedit the xorg.conf file.

BTW 1440x900 is the native res of that LDC.  I bought a 24" LCD with a native res of 1920x1200 and did the same to the xorg.conf and all worked perfectly.

---

### Post by J11Gyro on 2008-03-04
Not quite sure how to do all that but used the monitor settings onboard it to do a custom set up for all but windows.

---

### Post by StandardBlueCaboose on 2008-03-04
How to do all that:

First, do this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then execute this:

```
sudo gedit /etc/X11/xorg.conf
```

**or** in KDE:

```
sudo kate /etc/X11/xorg.conf
```

Enter your password and look in the text file for ' Section "Screen" .' It should look something like this.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"IBM 6652 P27"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1440"	"1600x1200"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
...
EndSection
```

I copied this from my own xorg.conf file, so yours will be different. After 'Modes' you can just insert your own "1440x900". 

Then just press ctrl + alt + backspace and it should restart your X session, and start gdm.

If that resolution isn't supported, it should just skip to the next one. If anything happens, and you are locked out, login and run the following command:

```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```

This will restore your old xorg.conf and you'll be back where you started.

Side note - Does running
```
nvidia-settings
```
do anything at all? If you don't see the resolutions there you might be using the nv driver instead of the nvidia driver.

---

