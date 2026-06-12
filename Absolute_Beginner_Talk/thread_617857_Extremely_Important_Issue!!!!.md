---
title: "Extremely Important Issue!!!!"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by mzdawg on 2007-11-19
OK this NEEDS to be fixed. It is just stupid. The resolution problems I`m having( And 1,000,000 other people) are keeping me from using Ubuntu, and to put it simply, my computer. At startup I sometimes have the error that says "The display has shut off 6 times"....etc. The res just keeps messing up! I change it with the xorg stuff and it works for a time, but when I reboot, my monitor either does not get a signal at all, or the screen is jumbled up.How can I can I keep it from changing???:confused:  

 I have the following things:

Sharp 26SH12U Monitor

ATI Radeon X1300 Graphics Card/ Have tried using the Vesa Driver, and the ATI driver

Ubuntu 7.10

PLEASE HELP, I`d rather use Vista if this keeps occurring. :cry:

---

### Post by MegaJim on 2007-11-19
First of all, please calm down - the people that will help you here are just other users like yourself and telling us something NEEDS to be fixed is like yelling at a wall.

Now, the problem you are experiencing, is this during the bootup process, once reaching the login screen, or once logging into an account?

---

### Post by mzdawg on 2007-11-19
Well, its kind of a mixed result. When its starts booting up and is about to go to the login screen, my monitor starts flickering and never gets to the desktop and I get the error message. When I do get to the desktop, it might be unreadable, or when it does work, when I reboot it changes again.

---

### Post by philinux on 2007-11-19
If your getting signal out of range open synaptic package manger and install startup manager. Once installed run it and set your desired resolution.

---

### Post by mzdawg on 2007-11-19
BTW i meant it needs to be fixed because there should be an update for this or something in the future, or the OS should be more user friendly. I wasn`t telling you guys it NEEDS to fixed. Sorry for the misunderstanding.

---

### Post by MegaJim on 2007-11-19
Have you previously tried to setup your monitor resolutions / frequencies by using

```
sudo dpkg-reconfigure xserver-xorg
```

If not I would recommend backing up your xorg.conf file and trying the above command then enter as specific information as possible about your monitor - it sounds like Ubuntu is trying to choose a bad frequency or resolution; 7.10 has some new features that try to protect against such things, but they are still a little "hit and miss"

---

### Post by mzdawg on 2007-11-19
Thx for the replies. :) Yeah I`ve always had 7.10 so I don`t know if earlier versions had this as well. But yes, I have configured the resolution in the terminal using that command MANY times. It always changes. Is there a way to keep it from changing or to save the changes, etc?

---

### Post by MegaJim on 2007-11-19
It could be that bullet-proof-x is being a poopy-head.

Please post the "Screen" sections from your xorg.conf file for the good members of this community to peruse.

We can try to persuade the monitor to behave, or perhaps disable bullet-proof X

---

### Post by mzdawg on 2007-11-19
How do I post those? I`m using a different computer for this. And I tried it again, and while booting it actually asked for the res, and now it is working. I  will go rebot to see if it changes.

---

### Post by MegaJim on 2007-11-19
open your xorg.conf file

```
gedit /etc/X11/xorg.conf
```

there will be a section beginning with "Screen"

for instance, on this laptop my xorg.conf screen section is:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I am interested in the display modes listed.

it might also help to include the "monitor" section so we can see the frequencies in use

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

```

for your reference, the technical specs of your monitor are located here: [http://www.sharpusa.com/products/ModelDetailedSpecs/0,1161,1842-,00.html](http://www.sharpusa.com/products/ModelDetailedSpecs/0,1161,1842-,00.html)

instructions for disabling bullet-proof-x can be found here: [https://answers.launchpad.net/ubuntu/+question/14320](https://answers.launchpad.net/ubuntu/+question/14320)

---

