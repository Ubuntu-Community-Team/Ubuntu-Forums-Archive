---
title: "changing screen resolution"
date: 2005-09-16
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-09-16
Does anyone know of a way to get more than 1024 x 768 screen resolution?

---

### Post by gordyt on 2005-09-16
Howdy racermike1967,

You probably need to edit your xorg.conf file, located in /etc/X11.  In particular, on my system I had to update this section:

```

Section "Monitor"
    Identifier          "Generic Monitor"
    Option              "DPMS"
    HorizSync           31-80
    VertRefresh         56-75
EndSection

```

You see the HorizSync and VertRefresh?  You need to find the proper values for the type of monitor you are using.  Note that the values in my example are for my monitor and will probably different for the one that you have.

Also, in the "Screen" section, you will see "Modes" lines for each of the different color depths.  If necessary you will need to add in the higher resolution(s) that you want to use.

In my case, the higher resolutions were already present in this file, but the system would not let me select the higher resolution until I fixed the HorizSync and VertRefresh values.

After editting this file you will need to restart Gnome.  See the [Ubuntu Starter Guide](http://ubuntuguide.org/#restartgnomewithoutreboot) for more info.

--gordy

---

### Post by jeffreyvergara.NET on 2005-09-16
hello, where can we get the information about our Monitor's HorizSync and VerRefresh?

---

### Post by aysiu on 2005-09-16
[QUOTE=jeffreyvergara.NET]hello, where can we get the information about our Monitor's HorizSync and VerRefresh?[/QUOTE] Usually the manufacturer's website will have a PDF manual for your monitor.

---

### Post by taxus on 2005-09-16
In my case I couldn't set the refresh frequency to anything else than 60 Hz. I couldn't find my manual, and I couldn't find any information about my Optiquest V73 on the Viewsonic web site. I did a Google search and came up with a 5 years-old Firingsquad.com review listing the specs. I love Google.

The article only listed the upper ranges though (70 max horizontal refresh and 110 max vertical refresh), so I left the lower ranges Ubuntu had written (30 and 43). I'd only tried changing the max vertical refresh to 120 before finding the article, and it didn't work. You really need the right figures for both vertical and horizontal refresh.

---

### Post by jeffreyvergara.NET on 2005-09-17
i don'y even know the model of my monitor... lol

---

### Post by jeffreyvergara.NET on 2005-09-17
[QUOTE=jeffreyvergara.NET]i don'y even know the model of my monitor... lol[/QUOTE]
 figured it out... woot

---

### Post by rjwood on 2005-09-19
I am a dummy-----I did fresh instll of breezy and only left on 640x480 resolution I unchecked the other 2 boxex that were of the higher resolution. Does anyone know what I can do????

---

### Post by jeffreyvergara.NET on 2005-09-19
[QUOTE=rjwood]I am a dummy-----I did fresh instll of breezy and only left on 640x480 resolution I unchecked the other 2 boxex that were of the higher resolution. Does anyone know what I can do????[/QUOTE]
 i don't quite understand... but if you want to add more screen resolution, open up Terminal>
then type: sudo gedit /etc/X11/xorg.conf > edit:

> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"7Vlr"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


then save it

I added all the 1280x1024, it works fine with me.

---

### Post by Xian on 2005-09-19
[QUOTE=rjwood]I am a dummy-----I did fresh instll of breezy and only left on 640x480 resolution I unchecked the other 2 boxex that were of the higher resolution. Does anyone know what I can do????[/QUOTE]
You can reconfigure your X settings whenever you like.
Just open a terminal and issue this command:

```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rjwood on 2005-09-23
Thanks guys :)

---

### Post by CaptainMorgan on 2005-09-23
Hi, 

Will this info on the xorg.conf file work the same for laptops as it does for monitors? 

I dock to an external old monitor, but when I use my laptop I would also like 1280x1024... I assume it would just relay to the monitor the same resolution... at least that what it does in Win. 

Thanks

---

### Post by CaptainMorgan on 2005-09-24
[QUOTE=jeffreyvergara.NET]i don't quite understand... but if you want to add more screen resolution, open up Terminal>
then type: sudo gedit /etc/X11/xorg.conf > edit:



then save it

I added all the 1280x1024, it works fine with me.[/QUOTE]

I erased every resolution but 1280x1024. Why isn't it forcing the new resolution? 

In my preferences list there is no option for it either... it still lists the lower three. 

Any suggestions?

---

