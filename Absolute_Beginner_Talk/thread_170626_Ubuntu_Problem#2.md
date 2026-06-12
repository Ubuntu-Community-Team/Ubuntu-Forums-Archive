---
title: "Ubuntu Problem#2"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by hellmet on 2006-05-05
The first time I had installed Ubuntu..everything went fine..
and I the VGA was detected succesfully.
But due to complications,I had to format my HDD.
Then again today, I tried to install Ubuntu.
It installed fine..but it did not ask wat resolutions to use.
And wen the installation was complete...all I cud use was the
640X480 resolution.
I am pissed off due to this..as I cant biew the top and bottom part of most of
the dialog boxes...and its a big annoyance.

Please help me guys..is there anyway to make it
detect my VGA??

BTW my MOBO is  Intel 915GAV.

---

### Post by joshrobinson on 2006-05-05
edit your xorg.conf file and add the resolution you need

sudo gedit /etc/X11/xorg.conf

in a terminal

it will pop up with the xorg.conf file.. scroll down to the section where you see the resolutions displayed.. and add the one you need in front of the others in the same format

heres what mine looks like.. find this section

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
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

then add in say 1024x768 if thats what you want in those spaces near the other resolutions in the same format
so after modes "1024x768"  "1280x800"

reboot and select your resolution in the screen resolution under system

---

### Post by K.Mandla on 2006-05-05
You might try typing this. ...

```
sudo dpkg-reconfigure xserver-xorg
```

into a terminal window. It will lead you step-by-step through reconfiguring the desktop; part of that is setting the screen resolutions you want.

Cheers!

---

### Post by skippy81 on 2006-05-05
Try running this in a terminal and see if you have any luck.

> sudo dpkg-reconfigure xserver-xorg

[Edit] someone got there first :)

---

### Post by hellmet on 2006-05-05
whoa...u guys are fast..
thanks guys..i'll try and tell you again.
Cheers to Ubuntu Community

---

### Post by joshrobinson on 2006-05-05
[QUOTE=hellemt]whoa...u guys are fast..
thanks guys..i'll try and tell you again.
Cheers to Ubuntu Community[/QUOTE]

their way might be easier for you then mine.. so do theirs first and if it doesnt work then do the way i said.. no file editing that way..

---

### Post by nanotube on 2006-05-05
and by the way, "ubuntu problem #2" is not very helpful. you should consider being more descriptive in your subject line (e.g., "low resolution upon install", at least.)
for a nice document with guidelines about this, check out the third link in my sig. :)

---

### Post by hellmet on 2006-05-05
People...I did as said to.

**sudo dpkg-reconfigure xserver-xorg**

It detected my board VGA easily.
I restarted.
No use...still the only available res. is 640X480

then I used JoshRobinson advice.
Again Restarted.
Still of no use...
In the xorg.conf,
I cud see the Monitor as 107E(Philips)
and VGA 915gav during Xserver reconfiguration.

Please help guys.

---

### Post by hellmet on 2006-05-05
Yaa I got it people...
Its working fine now.

Both my monitor and chipset VGA are recognised.

Thanks a lot people.
You were the most helpful.

---

### Post by nanotube on 2006-05-05
[QUOTE=hellemt]Yaa I got it people...
Its working fine now.

Both my monitor and chipset VGA are recognised.

Thanks a lot people.
You were the most helpful.[/QUOTE]
so what did you do to make it work?

---

