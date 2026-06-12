---
title: "[SOLVED] Serious Problem? - xorg.conf missing or invalid"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-03-12
Hi!

I was forced to reboot my computer. Everything was working just fine. Once i tried to install compiz and it didn't work but i wasn't worrying so much about it. No i after rebooting my computer the fancy window effects (windows are more or less flying in and so on) are gone.
I remember that they appeared when i activated the alternative drivers for my nvidia graphic card. So I tried to activate them again and now it says that it is not possible because /etc/X11/xconf.org is not valid or missing. (My system language is Swedish and i'm not quiet sure about the translation but this is basically what it says)

Did someone have similar problems?

Thomas

---

### Post by glennric on 2008-03-12
Type in a terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by itix on 2008-03-12
Psss... det är illa för supporten att ha det på svenska, dessutom lär du dig inget :p

It's quite the problem actually. xorg.conf contains a lot of system settings, one of which is the screen settings and graphics card settings. Post the screen section of xorg.conf-file
mine looks like this: 
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	.	
	.
	.
EndSection

```

code for viewing xorg.conf
```
gedit /etc/X11/xorg.conf
```

---

### Post by thomas7.10 on 2008-03-12
...Jag håller med för supporten är det inte så himla bra men jag lär mig åtminstone lite svenska - egentligen är jag tysk ;)

Surprisingly i have 3 xorg.conf files. They are called xorg.conf.1, xorg.conf.2, xorg.conf.original-0. No i don't know which to choose.

In xorg.conf.1 i have these configurations:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 LE]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

```

In xorg.conf.2 I have these:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 LE]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@43"	"1152x864@75"	"1024x768@60"	"1280x960@60"	"1024x768@70"	"1280x1024@60"	"1024x768@75"	"1400x1050@60"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

```

And then i have xorg.conf.original-0 with the same settings as in xorg.conf.1

Would it be a good idea to run that command?:
```
sudo mv ./xorg.conf.2 ./xorg.conf
```


By the way does someone know a good guide to get compiz with this box module to run on gutsy or is it really complicated?

Thomas

---

### Post by alexforcefive on 2008-03-12
> **thomas7.10 said:**
> Would it be a good idea to run that command?:
```
sudo mv ./xorg.conf.2 ./xorg.conf
```

sudo cp might be a better idea, but either way it should solve your problem. Make sure all the settings are correct before you use it though ;)

---

### Post by itix on 2008-03-12
Box module?? 

And I think
```
sudo cp /etc/X11/xorg.conf.2 /etc/X11/xorg.conf
```
is better...

Have you checked the rest of the settings in the file?? It's quite crucial that they are not changed.

---

### Post by thomas7.10 on 2008-03-13
It worked!

Thank you!

Tack så mycket!

---

### Post by itix on 2008-03-14
Schysst att det löste sig... Se till att makera tråden som löst så att andra med samma problem kan hitta den lättare ;)

---

### Post by thomas7.10 on 2008-03-15
Det skulle jag göra om jag visste hur.

edit: Ok klart

---

