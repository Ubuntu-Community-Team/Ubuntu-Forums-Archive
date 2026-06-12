---
title: "I've tried everything I can think of....(monitor issue)"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Marklinh89 on 2007-07-06
I really can't seem to figure out what to do here.  I just can't get it too it's native resolution.  I've tried booting into the terminal and running the reconfigure command, and it still didn't work.  


Here's a screen of what it looks like.

[http://img372.imageshack.us/my.php?image=screenshotyr6.png](http://img372.imageshack.us/my.php?image=screenshotyr6.png)


I'd really appreciate some help, thanks.

---

### Post by enopepsoo on 2007-07-06
have you tried editing your xorg.conf file directly?  It is pretty self explanatory.  You might try just editing that and restarting xorg.

```
sudo gedit /etc/X11/xorg.conf
```

Find the section where resolutions are specified and add yours in.

```
sudo /etc/init.d/gdm restart
```

restarts your x server.

Best of luck to you.

---

### Post by overdrank on 2007-07-06
> **Marklinh89 said:**
> I really can't seem to figure out what to do here.  I just can't get it too it's native resolution.  I've tried booting into the terminal and running the reconfigure command, and it still didn't work.  


Here's a screen of what it looks like.

[http://img372.imageshack.us/my.php?image=screenshotyr6.png](http://img372.imageshack.us/my.php?image=screenshotyr6.png)


I'd really appreciate some help, thanks.

Hi you will have to edit your xorg, by using this command in the terminal, located under applications, accessories, terminal
```
gksudo gedit /etc/X11/xorg.conf
```
Then scroll down to the screen section that will look like this (not exactly)
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
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
And then you can add the resolution that you want to each line and dont forget the " " and then save.
Hope this helps and good luck! :D

---

### Post by Marklinh89 on 2007-07-06
> **overdrank said:**
> Hi you will have to edit your xorg, by using this command in the terminal, located under applications, accessories, terminal
```
gksudo gedit /etc/X11/xorg.conf
```
Then scroll down to the screen section that will look like this (not exactly)
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
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
And then you can add the resolution that you want to each line and dont forget the " " and then save.
Hope this helps and good luck! :D



This was actually the first thing I tried.  But when I got to "Preferences>Screen Res." It doesn't show the resolution there.  And in the Nvidia settings, It still the same resolutions.


Thanks again for the fast replies.  Any more ideas ^_^?

---

### Post by whiteguysamurai on 2007-07-06
Have you tried to reconfigure your xserver?

Here, try this
```
sudo dpkg-reconfigure xserver-xorg
```
After that, after you tell it what video driver you really have, make sure you have the proper resolutions posted.
Then use the simple disply wizard, it will ask you what kind of monitor size you own,
Then restart and it should be set up.

Also, if not use the Crtl-alt-+/- to switch formats.

Best of luck.

---

### Post by Marklinh89 on 2007-07-06
I tried that too ;-;

---

### Post by overdrank on 2007-07-06
> **Marklinh89 said:**
> I tried that too ;-;

Well just to throw it out there, have you tried a restart after each of those. And I mean not a restart x by ctrl,alt, backspace but and full restart?

---

