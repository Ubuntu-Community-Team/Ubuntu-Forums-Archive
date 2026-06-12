---
title: "Driver troubles"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by crackling on 2006-11-18
Edit: I forgot to mention I am also using a Dell laptop.
Okay, so I have just installed Ubuntu 6.06 and I love it so far, I just have a few problems. 

I can't seem to install my graphics driver, I have a Intel Integrated Graphics Media Accelerator 950 GM. I have found the driver but I have no idea how to install it. When I open it, the Archive Manager opens and I extract it to my desktop (it looks like a regular folder from Windows and I can't find anything inside that will install) and that's where I'm stuck. The reason I want the driver is because my monitor is capable of higher resolution but I can't change it currently. This is as far as I got:
[IMG]http://img175.imageshack.us/img175/640/screenshotqr9.png[/IMG]


Also, I am having some wireless troubles, I have a Intel PRO/Wireless 3942 802.11a/g Mini Card(54mbps). My regular NIC works fine but my wireless doesn't want to work, in Network settings it says:

> 
Wireless connection
The interface eth1 is active


but I am not getting any internet, and the only connections showing in Connection properties is eth0 my regular NIC and lo. This is what I get from iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any
          Mode:Managed  Frequency:nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:off
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:250   Missed beacon:0

sit0      no wireless extensions.

```

Any help is appreciated. :-k

---

### Post by crackling on 2006-11-18
I'm still unable to resolve these issues, help please.

---

### Post by nekr0z on 2006-11-18
Concerning your video driver: if you *really* want to install it, try reading the README file, the one that can be clearly seen on the screenshot you provided. If I were the one to write that driver, I would call the file that explains how to install it README...

But personally I do think that installing a driver from sources is *not* a good idea, unless you *really* have no other choice. I would try tinkering with /etc/X11/xorg.conf to see if higher resolution can be achieved before installing something new.

Now to your wireless problems: "radio off" is the first thing I would try to manage. As far as I understand, you wireless card can be switched on and off, either by a hardware switch or in some software way. I don't own a Dell, so I can only guess: it's not a hardware switch on the side of the laptop you've forgotten to pun ON, right?

Software radio switching is always a p.i.t.a. in Linux world. Have you tried googling this issue? I have had the similar problem on my Fujitsu-Siemens, and [here]("http://www.ubuntuforums.org/showthread.php?t=189540") is how I solved it. Try reading this, maybe it gives you some ideas of how to deal with your problem, or at least just some ideas of what to google for...

---

### Post by crackling on 2006-11-18
I can't seem to get /etc/X11/xorg.conf to work.

```
bash: /etc/X11/xorg.conf: Permission denied
```

Also, I don't have a on/off switch that I could fine and wireless has worked for me fine before with Windows. It seems I switched it off with the Fn key, I it back on and got this via iwconfig:

```
unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid] frag:0
          Tx excessive retries:0  Invalid misc:660   Missed beacon:0


```

It's an improvement but I am still getting no internet.

---

### Post by junglepeanut on 2006-11-18
Try using network-admin part or network-manager

I like network-admin

Also

Have you set the wireless to your account

use 

man ifconfig
or
man iwconfig 

to see all the different options you can specify

to mess with x11

use an editor

I like vim
but since you are fairly new try gedit

then editing /etc/X11/xorg.conf can make things very bad so it is protected so if you want to change it do 

sudo gedit etc/X11/xorg.conf

also before doing that try

sudo dpkg-reconfigure xserver-xorg 
and make sure all of the option are what you want

---

### Post by crackling on 2006-11-18
From sudo gedit /etc/X11/xorg.conf this is what is relevant:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
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

```

```
Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

```

I am currently running at 1024x768 resolution on a widescreen, I'm not quite sure if the driver is correct. The driver I downloaded was for the Intel 945 chipset and is i386 but from the code the driver currently installed is i810. Also, when running sudo dpkg-reconfigure xserver-xorg there is no i386 driver option.

Also, I would like to mention that my Wifi LED is blinking very rapidly but I am not getting internet.

---

### Post by nekr0z on 2006-11-19
Don't be confused about i810 driver: if you read the manual ("man i810") you see that it suits for Intel 945 too.

Your problem here could be that X.org thinks your monitor is not capable of higher resolutions, while the video card is. I would try to put in the modeline for necessary resolution manually. Google it up for "x.org modeline"  and read a bit on how to arrange the things here.

Concerning your wifi, the blinking LED means that your radio itself does work, so the problem is only to get it connected. I would advise installing network-manager-gnome from Synaptic and getting online with this tool.

---

