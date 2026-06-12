---
title: "screen res for wide screen"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by unseenbeing on 2006-09-06
i just downloaded ubuntu cause i read about it in a magazine (it looked good so i thought i would try it out)
i have no experience with linux

how would i change my res to be 1440x900

explain it like you would talk to your mom about the internet

---

### Post by empcrono on 2006-09-06
> **unseenbeing said:**
> i just downloaded ubuntu cause i read about it in a magazine (it looked good so i thought i would try it out)
i have no experience with linux

how would i change my res to be 1440x900

explain it like you would talk to your mom about the internet

Did you check out system/prefernces/screen resulution?

if not go to the top of the screen your see right next to the fire fox icon 
System click on that and roll your mouse over to prefernces then find screen resulution and click it.

---

### Post by unseenbeing on 2006-09-06
yes i did that its not an option

i keep seeing posts about editing some file but i dont know how or even where to start

i dont know the model of my monitor i know its a princeton 20.5" widesreen

---

### Post by benfindlay on 2006-09-06
to edit the config files, you need to launch terminal and type: ```
gksudo gedit /etc/X11/xorg.conf
```

This will prompt you for your password, then it will open the configuration file in gedit (a text editor similar to notepad in windows)In here you need to look through the file till you find a list of resolutions. Just add your desired resolution to the lists There will be multiple lists, for each colour depth your setup supports, so just add "[width]x[height]" to each one.

Then reboot, and it will either boot up in your new resolution, or allow you to change it in the options menu mentioned in previous posts.

Hope this helps!

---

### Post by Druidor on 2006-09-06
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index....0Configuration](https://wiki.caosity.org/tiki-index....0Configuration)

---

### Post by unseenbeing on 2006-09-06
k i did the edit the res that benfindlay said
it did nothing

do i have to install a driver of some kind?
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by unseenbeing on 2006-09-07
i got it working
i found the drivers for it and it works like a peach
thanks to all that helped

---

