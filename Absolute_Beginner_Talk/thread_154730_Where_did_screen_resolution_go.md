---
title: "Where did screen resolution go?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-03
I restarted my computer, and I realized that now I only have 640x480 screen resolution. The other options just disappeared. How can I get those back? Thanks!

---

### Post by taurus on 2006-04-03
You can modify, as root with sudo, /etc/X11/xorg.conf...
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by The Mekon on 2006-04-03
To expand on taurus's post when you open xorg.conf look for something like my pasted input and type in what resolutions your monitor can handle:

Pasted from my xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"15 COLOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

End of Pasted section:

Type "man xorg.conf" in a terminal to get a further understanding.  Scroll down to the Screen Section

Brian

---

### Post by catlett on 2006-04-03
If you can't solve it by editing, you can go back and reconfigure your settings. It's best to search for a manual on your monitor so you will know the refresh limits and color depth etc. The more info you put in during the configuration, the better resolution detection you'll get. Do this command. 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by amitroy5 on 2006-04-03
I guess if something is wrong, restart the computer. I restarted Ubuntu and everything came back. Thanks everyone! :)

---

