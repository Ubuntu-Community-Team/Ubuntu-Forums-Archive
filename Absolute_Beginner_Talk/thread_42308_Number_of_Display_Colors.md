---
title: "Number of Display Colors"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by sscotti on 2005-06-16
I'm just getting started with Ubuntu and I noticed that I can't find a place to set the number of colors on the display with the tools that I can see.  Is there a way to change the number of colors that are displayed and the screen resolution.

Thank you.

---

### Post by Xian on 2005-06-16
That is set in the /etc/X11/xorg.conf file.
The maximum default depth is "24".

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"COMPAQ 7500"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```

Read [X11 Config](http://www.slackersbible.org/node/80) for more info.
Here's an excerpt:

[i]Please specify which color depth you want to use by default:

1 1 bit (monochrome)
2 4 bits (16 colors)
3 8 bits (256 colors)
4 16 bits (65536 colors)
5 24 bits (16 million colors)

Enter a number to choose the default depth.

Here you pick how many colors you want displayed. If you are not sure, most cards and monitors are capable of 16bit and 24bit color. However, remember that some graphics cards cannot perform acceleration at 24bit.[/i]

---

