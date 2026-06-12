---
title: "Portrait Format"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Graybeard on 2006-11-03
This is a post from a newbie, for newbies, explaining how I got portrait format at a specified screen resolution to work. It is not so much a How-To as a How-I-Did-It. It worked for me. That means it worked on a Dell Dimension 4550 with a 64MB GeForce4 MX Graphics card and a ViewSonic VP920b monitor running Ubuntu 6.06 LTS. "Your mileage may differ."

The benefits for my purposes are:
1: It displays in portrait format, which I prefer for the kind of work I do.
2: It allows a choice of screen resolution, which my aging eyes appreciate.

The disadvantages as I see them are:
1. It disables on-the-fly resolution changes via System>Preferences>Screen_Resolution.
2. It slows down screen refresh slightly.
3. It doesn't allow easy switching from portrait to landscape or vice-versa.

The steps I took (without the missteps):

1. I opened a terminal/command-line window (Applications>Accessories>Terminal)

2. I changed to the necessary directory:
[HTML]bob@bob-dell:~$ cd /etc/X11/[/HTML]

3. I made a backup of the existing xorg.conf file:
[HTML]bob@bob-dell:/etc/X11$ cp xorg.conf xorgBU.conf[/HTML]

4. I opened xorg.conf in a text editor:
[HTML]bob@bob-dell:/etc/X11$ sudo gedit xorg.conf
Password:[/HTML]
Note: When you enter your Ubuntu password, *nothing* will appear on the screen. Don't retype it. Just hit enter.

5. When xorg.conf appeared in the editor (gedit) I scrolled to the part that read:
[HTML]Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection[/HTML]

6. I edited it to read:
[HTML]Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
#The following line added to provide "portrait" format display.
	Option		"Rotate" "CCW"
EndSection[/HTML]

7. I then scrolled to the section that read:
[HTML]Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"VP920 Series"
	DefaultDepth	24[/HTML]
and noted that the "DefaultDepth" was "24"

8. I scrolled down to where it read
[HTML]	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection[/HTML]

9. I edited it to read:
[HTML]#	SubSection "Display"
#		Depth		24
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection

#The following subsection replaces the above subsection in order to force screen
#resolution to 1024x768.

	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection[/HTML]

10. I "saved" the changes, closed the editor, rebooted, and found Ubuntu in Portrait format at 1024x768 resolution. 

In actual practice I got here by trial and error and after one misstep I rebooted to find a slew of error messages, no GUI, and a command-line. To recover, I restored the original xorg.conf by entering:

[HTML]bob@bob-dell:~$ sudo cp /etc/X11/xorgBU.conf /etc/X11/xorg.conf[/HTML]

and then rebooted.

Final note: It has taken me a lot of time to wade through "help" that was way over my head. Hopefully, this post is explicit enough to help others as inexperienced as I am. Those with more experience are more than welcome to suggest better ways to achieve these results, or acheive better results, but please explain in a way that those who need the advice can understand it. A lot of us are ignorant; not stupid, just ignorant. We don't get educated from advice we don't understand or can't follow.

bob

---

### Post by jpeddicord on 2006-11-03
That's a pretty good howto, and I do think it will help a bunch of users that want to use vertical resolutions.
Nice work!

Jacob

---

### Post by holiday on 2007-08-10
Thanks Greybeard. It works.

Except now I can't get out of portrait unless I change xorg.conf and reboot. At least I'm thinking I can. Right now I'm getting a neck cramp.

When I try to access my resolution preferences through the menu, I get 
"The xserver does not support xrandr extension. Runtime resolution changes to the display size are not available."

Trying xrandr from the console gets me "core dump"

Ideas? 

Anyone?

---

### Post by holiday on 2007-08-11
Ah, I see that this is a common problem with rotate, and that the manual switch of xorg.conf and  xserver restart is the standard solution. As soon as I added "rotate" to my search query I became witness to a world of pain.

But here is hope:

[https://wiki.ubuntu.com/Xorg7.3Integration](https://wiki.ubuntu.com/Xorg7.3Integration).

---

