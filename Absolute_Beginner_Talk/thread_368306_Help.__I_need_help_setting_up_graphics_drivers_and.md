---
title: "Help.  I need help setting up graphics drivers and monitor"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by geoffcj on 2007-02-23
Help!  

I love the idea of the opensource movement, am fairly technically adept, but completely new to Linux/ubuntu.   

Today I put together a new PC, using a Elite Group P4M800PRO-M  motherboard and a Pentium D processor.  It has a built in graphics card, S3 Graphics UniChrome Pro IGP Video. 

I also picked up a Norcent 19" widescreen monitor, with native resolution 1440x900.   

My problem is, Linux is up an running, but looks like CRAP.  

I think I need to install drivers for the card, but don't have a clue how to do it.  And I need to get ubuntu to offer the resolution I need for this monitor. 

Can somebody help me?  I need step by step instructions on how to find and install the graphics driver.  Remembering I've been using Linux for about 7 hours! (mostly futzing with the graphics!) 

And then instructions on how to change the resolution?  I can get to a screen settings control panel, but it only offers a few choices for resolutions, none of which are what I'm looking for. 

Thanks, 
Geoff

---

### Post by renzokuken on 2007-02-23
welcome to ubuntu

run the following command from a terminal

```
sudo dpkg-reconfigure xserver-xorg
```

this will bring up a basic grafix configuration utility with various options. just select the default values for each option as they come up, and when you get to the "resolutions" screen, use spacebar to add the necessary resolutions (put a * next to the options....you will understand when you see it). leave all other options as they are.

when its finished exit the terminal and press Ctrl+Alt+Backspace to restart the x-server. log back in and see if you have the option of the new resolutions

---

### Post by geoffcj on 2007-02-23
So here's a stupid question, but I got the screen you mentioned, but how do I put the * in?   No obvious key's did

---

### Post by renzokuken on 2007-02-23
try using the space bar. can you scroll through the resolutions though using the arrow keys?

---

### Post by geoffcj on 2007-02-23
Ok, so through some combination of your suggestions, and some other hints I found online, my screen looks better.   It's displaying at 1280x768 though, which is smaller than I'd like.  (I'd like to go even bigger than 1440X900, but that's the native resolution of my monitor. ) 

I had few crashes when I tried the method used above, after restarting X would refuse to start. I restored it by reverting to a saved version of my xorg.conf file. 


I manually adjusted some settings in my xorg.conf according to some instructions I saw elsewhere.    Like I said, it looks OK now, but smaller than I'd like. 

Here's the relevant part of my xorg.conf file.  

"
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        Option          "DDC" "false"
        Modeline        "1440x900" 106.5 1440 1520 1672 1904 900 903 909 934
	HorizSync	30-56
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" 
	EndSubSection
EndSection"



Any Help appreciated!!!!!!!

---

### Post by renzokuken on 2007-02-23
it may well be that the vesa driver doesnt support a resolution that high.

although vesa is very reliable, its not great on performance. did you say you have onboard grafix or a grafix card? any idea which chipset that card is based on, intel, ati, nvidia?

if you know which we can tell you how to install the specific driver driver for it o improve performance

---

### Post by geoffcj on 2007-02-23
The graphics are built into the motherboard. 

P4M800PRO-M motherboard and a Pentium D processor. It has a built in graphics card, S3 Graphics UniChrome Pro IGP Video

Thanks! 
Geoff

---

### Post by geoffcj on 2007-02-23
Well, I've now been using Linux for about 14 hours of futzing, and my monitor still looks like crap.  

I guess there is a reason windows is still in business.  Somebody not fully commited would have given up long before this! 

=<
Geoff

---

### Post by caintona on 2007-02-23
Yeah this is the biggest problem i have found with linux.  Setting up your video too look decent.

The problem is the vid card companies don't work with the open source community to develop solid drivers for the platform.

At least that is what it seems to this guy.

---

### Post by caintona on 2007-02-23
Also I have discovered that nvidia cards perform much better than ati cards.

at work im runnning dual screens on my laptop and a seperate monitor with nvidia quadro

at home running 1920x1200 on a 27inch monitor with ati card(this was a pain in the *** to set up)

---

### Post by Nythain on 2007-02-23
hehe... setting that machine up on windows would look like crap untill you installed something bettter than 6 year old generic windows drivers also... its just a little easier on windows... Its a via chip, id suggest looking for drivers for it... ok just googles for 90 seconds and synaptec one search found that you should make sure you have xserver-xorg-video-via installed and possibly change the line in your xorg.conf from vesa to via... not sure if the driver itself needs any configuring... be sure to back up xorg, give it a try and let us know

---

### Post by geoffcj on 2007-02-23
Tried that, X windows wouldn't restart (crashed).  

Went back to my backup xorg file. 

Ugh.  

Starting to look around for my XP disks...

=<
Geoff

---

### Post by fenderjaguar on 2007-02-23
when you run that command line, that the second poster wrote for us, is that all you need to do? because there seem to be nvidia drivers in synaptic. does anybody know if i should install any of those? my video card is a nvidia geforce fx 5200...

---

### Post by Nythain on 2007-02-23
im sorry i cant be much more help, i never had any luck with integrated graphics, in windows or linux... in fact i've never had much luck in windows period... my analogy, windows will do more out of the box, but when you encounter a problem, your screwed, linux you will encounter more problems, but you have every tool and option available to fix the problem...

i would continue to google your problem cause i hate to see people go back to windows because of a problem i know there HAS to be a solution to... but alas, i have to go to work...

---

### Post by docshawnc on 2007-02-23
Have you tried this driver: [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=109)

maybe of some help

---

### Post by geoffcj on 2007-02-23
Mostly Fixed.   I installed a new Nvidia video card, reinstalled Linux,  and it's mostly working now, even in 1440x900 

But the fonts look like crap.  It's set to Sans, and I have the smoothing option set, but it's virtually unreadable.  Pictures and graphics look ok.  I'm going to post in a new thread...

Geoff

---

### Post by renzokuken on 2007-02-24
install the latest nvidia drivers, have a look at [www.albertomilone.com](www.albertomilone.com) (projects and guides) for two very easy ways to do it) this will improve performance no end, allow higher resolutions and solve the blurry font problem

---

