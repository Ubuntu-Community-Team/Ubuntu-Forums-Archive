---
title: "Powermac dual 867 questions"
date: 2008-03-21
forum: Apple PPC Users
---

### Post by Snapcase on 2008-03-21
Hi all.

I used Dapper for a while in a laptop PC untill it died. Time passed and I forgot about anything about using Linux. So I'm about a newbie again.

I plan to install Ubuntu in my Powermac Dual 867 for multiple boot (I already got three different OS installed here, OS9, Panther and Tiger, and I want to boot in them all). I currently have a partition unused I made to try Digital Performer wich I din't liked so much, so I forgot about it. I'd like to install Ubuntu Studio but it seems it's not ready for PPC for now and involves compiling a new low latency kernel, Am I right? Well, I'll try this later, I'll have to make it all working first.

My questions are. Should Ubuntu be installed in an specific HD or partition or any would work? Will it recognize my two monitor screens? How should i manage to configure that multiple boot? Will it recognize the Motu 828 or Digi 003 sound cards?

Thanks.

---

### Post by Snapcase on 2008-03-21
I managed to install Feisty (the Gutsy iso failed to install twice). Feisty installed and booted without problems but the system runs really slow compared with Tiger. Opening a simple window takes a long while when in Tiger it just takes an instant. Is this normal? Also I've found a lot of things that doesn't work: No sound, no dual monitor, no caps and number locks on keyboard, no way of changing appearance... (it shows error alerts when I try to configure any of these things).

I think I'll install Kubuntu instead, I'm much more familiar with KDE (I used Kubuntu Dapper) and I feel a bit lost in the Gnome enviroment.

---

### Post by slacka-vt on 2008-03-21
You should have absolutely no issues installing Hardy pre-release on that.
I have it running on both a PowerBook G4 1GHz with 768 RAM and a
PowerMac G5 Dual 2.7Ghz 5GB RAM.
The speed seems quicker then Mac OS X on both systems.
Definitely a noticeable difference.
I've "tinkered" with ubuntu for a few years,
but the Hardy distro has actually made me convert.
It does everything I need my machine to do quicker,
and with less "clutter"
 
~s

---

### Post by Snapcase on 2008-03-22
Well, a bit too late... Thanks anyway for the advise.

I got Kubuntu Feisty running. Much better and agile than my previous install. Still a lot of work to do and a lot of things to solve, but quite happy.

How to make my two monitors running? Curently the Apple Studio 17" is working but the ViewSonic 19" doesn't seem to be recognized.

---

### Post by slacka-vt on 2008-03-22
maybe try running in your terminal:

sudo dpkg-reconfigure xserver-xorg

this will open up a monitor / display configuration dialog.

should be a good start at least.

~s

---

### Post by Snapcase on 2008-03-23
I'll need to boot OSX to check the videocard parameters this configuration dialog is asking for. Hope it works. Thanks a lot.

About sound. I got sound working but didn't noticed until now. I read in this forum that sound should be expected weaker than in OSX, but It sounds softer than the computer fans noise! I needed get my ear really close to the speaker to check it. System volume is set at 100%. Is it possible setting sound to an usable and logical level?

I'm not sure if the two processors are being used. I made a couple of checkouts I found around here, but I really don't know what confirms they both are actually working.

Thanks in advance.

---

### Post by oswaldkelso on 2008-03-23
> **Snapcase said:**
> Well, a bit too late... Thanks anyway for the advise.

I got Kubuntu Feisty running. Much better and agile than my previous install. Still a lot of work to do and a lot of things to solve, but quite happy.

How to make my two monitors running? Curently the Apple Studio 17" is working but the ViewSonic 19" doesn't seem to be recognized.

I have a g4 867 powermac. not dual but running twin monitors on debian my graphics card is a ati 9800 pro and my monitors are different but looking at the attached my xorg.conf may help you my set it up. Its a big screen i.e two monitors as one.

---

### Post by Snapcase on 2008-03-23
Thanks for your input. I tried to follow your steps, but it still doesn't work. Here are my current xorg.conf video sections

```
Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:0:16:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 420] (Secondary)"
	Driver		"nv"
	BusID		"PCI:0:16:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Apple Studio"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"VX2025wm"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"Apple Studio"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1272x1017"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Secondary Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 420]"
	Monitor		"VX2025wm"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1272x1017"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1272x1017"
	EndSubSection
EndSection
```

I don't know the adecuate settings for the ViewSonic VX2025wm so I copied the Apple Studio settings and crossed my fingers, but after rebooting nothing changed. Any idea?

BTW: What depth means? I don't find this data in the monitor specs papers.

---

### Post by oswaldkelso on 2008-03-23
Some links and an xorg.conf file to look at one thing to check is where screen0 and screen1 are in relationship to your setting or you may find your curser going off the left hand side to come on the right!

please check this gift horses teeth before accepting, I don't want you to blow up your monitor 

[http://www.viewsoniceurope.com/UK/Products/LCDX/VX922.htm](http://www.viewsoniceurope.com/UK/Products/LCDX/VX922.htm)

[http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-refresh-rate-and-viewsonic-vx2025wm-487545/](http://www.linuxquestions.org/questions/linux-hardware-18/xorg.conf-refresh-rate-and-viewsonic-vx2025wm-487545/)

---

### Post by Snapcase on 2008-03-23
Thanks so much. I'll check all this and try to understand what all these parameters changes imply.

---

### Post by stream303 on 2008-03-24
> **Snapcase said:**
>  Is it possible setting sound to an usable and logical level?

I'd run alsamixer in a terminal, and see if your PCM is at too low a level.  Also check the default ouput levels in the various sound programs.  Sometimes they differ from the default system setting.

> I'm not sure if the two processors are being used. I made a couple of checkouts I found around here, but I really don't know what confirms they both are actually working.

A nice reassuring graphical way is to download HTOP, and run that from a terminal.  It will quickly identify both cpus and if they are in use.

---

### Post by Snapcase on 2008-03-25
Thanks for your advices. The two processors are working.

About sound, I've run Alsa mixer and found I got the PCMs set at 80%. I raised them to 100% and works better. Still not the output under OSX. Way softer, but I think I can live with it. Anyway any other help in order to increase the output level a bit will be welcome.

Thanks a lot.

---

### Post by stream303 on 2008-03-27
Something to check - and it is coming from left field and is a total guess on my part - does it make any difference if you plug into the line-output instead of the speaker output?  Doesn't make sense though does it?

I've had my share of Linux (even FreeBSD) sound drivers in the past reverse these two jacks making me go insane, because they worked perfectly on Windows or OSX.

Just a wild guess....

---

