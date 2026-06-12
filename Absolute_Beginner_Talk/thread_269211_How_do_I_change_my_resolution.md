---
title: "How do I change my resolution?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Speedycat on 2006-10-01
Well, I need some help with changing my resolution.

Now my video card can go up to 1280x1024, and I want to use 1152x864 like my windows used to have.

I've edited my xorg.conf to include my desired resolutions, but the only way I know to change resolution is "System>Preferences>Screen Resolution"

That still lists only "640x480, 800x600, 1024x768" and ONLY one refresh rate.

Is there a different way to set my resolution that I haven't found yet?

---

### Post by bodhi.zazen on 2006-10-01
Edit xorg.conf:```
sudo gedit /etc/X11/xorg.conf
```

In the "screen" section, add an entry "1152x864.

Like this:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"twinview"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
**		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"**
	EndSubSection
	SubSection "Display"
		Depth		24
**		Modes		"1280x1024" "1152x864" "1024x768" "960x529" "832x624" "800x600" "720x400" "640x480"**
	EndSubSection
EndSection

Don't worry about the rest of the section, this is from my xorg.conf and is an example only ! 8-)

After editing xorg.conf you need to restart X:

Use the three finger salute: Ctrl-Alt-Backspace. This will bring you to the log in screen (GDM).

You can then change resolutions using the Ctrl-alt-+ combination.
(Ctrl and Alt and the "+" on your number pad). 8-)

---

### Post by sbergman27 on 2006-10-01
If after you have edited the xorg.conf file and rebooted (or otherwise restarted X) you still don't have higher resolutions and refresh rates available, then the monitor frequency settings could be incorrect in xorg.conf.

What is the brand and model number of your monitor?

---

### Post by cmaranhao on 2006-10-01
there is a similar thread here:

[http://www.ubuntuforums.org/showthread.php?p=1567607#post1567607](http://www.ubuntuforums.org/showthread.php?p=1567607#post1567607)

and my question remains the same:

how do i save the changes?

---

### Post by Speedycat on 2006-10-01
> **sbergman27 said:**
> If after you have edited the xorg.conf file and rebooted (or otherwise restarted X) you still don't have higher resolutions and refresh rates available, then the monitor frequency settings could be incorrect in xorg.conf.

What is the brand and model number of your monitor?

How would I go about finding that out? My monitor doesn't really say what brand/model it is.

Should I look on the back?

---

### Post by sbergman27 on 2006-10-01
Yes, look on the back. It's got to say somewhere.

---

### Post by Speedycat on 2006-10-01
> **sbergman27 said:**
> Yes, look on the back. It's got to say somewhere.

The type/model is 6332-01N

Honestly, there is no Brand name on the back or front of the monitor

---

### Post by sbergman27 on 2006-10-01
Is this it?

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4GXSCC](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4GXSCC)

---

### Post by Speedycat on 2006-10-01
It doesn't say "IBM" on it like that picture, but it certainly does have the same serial number.

---

### Post by sbergman27 on 2006-10-01
OK.  So you have rebooted since editing the file, right?

---

### Post by Speedycat on 2006-10-01
Several times. I'm not *that* stupid :3

---

### Post by sbergman27 on 2006-10-01
OK.

Make a copy of the /etc/X11/xorg.conf file just in case.

Then look in the file and look for 2 lines that look something like this:

HorizSync       30.0 - 97.0
VertRefresh     50.0 - 180.0

The numbers will be different.  What are they?

---

### Post by Speedycat on 2006-10-01
Okay, well my monitor obviously is one of those IBM's for sure now.

Here is what my section says
Section "Monitor"
	Identifier	"IBM E74"
	Option		"DPMS"
EndSection

However, even with ctrl+F I couldn't find the HorizSync or VertRefresh part in xorg.conf. 

This could be my problem >:P

---

### Post by bodhi.zazen on 2006-10-01
> **sbergman27 said:**
> OK.  So you have rebooted since editing the file, right?

There is no need to re-boot unless he has installed drivers (like nvidia or ATI).

> **Speedycat said:**
> It doesn't say "IBM" on it like that picture, but it certainly does have the same serial number.

You are a fast cat as we have seen from prvious posts of yours.

Can you tell me, did you edit xorg.conf? If you did, next check you monitors horizintal and vertical refesh rate. This is in the "monotor" section of xorg.conf:
> Section "Monitor"
Identifier "Monitor1"
VendorName "IBM"
ModelName "IBM P260"
[b]HorizSync 29-121
VertRefresh 50-180[/b]
Option "DPMS"
EndSection

DO NOT USE MY NUMBERS. You will need to google to find the numbers for your monitor.

If that fails, reduce the color depth from 24 to 16 (AKA "DefaultDepth" in your "Screen" section).

If that does not work, you may need to insall a driver. What video card are you using?.

---

### Post by Speedycat on 2006-10-01
> **bodhi.zazen said:**
> There is no need to re-boot unless he has installed drivers (like nvidia or ATI).



You are a fast cat as we have seen from prvious posts of yours.

Can you tell me, did you edit xorg.conf? If you did, next check you monitors horizintal and vertical refesh rate. This is in the "monotor" section of xorg.conf:


If that does not work, you may need to insall a driver. What video card are you using?.

In the first post I already said I edited xorg.conf :3

My monitor section is nearly empty with no refresh rate in the section, and I'm using an "Intel express chipset family 910" card.

---

### Post by sbergman27 on 2006-10-01
> **bodhi.zazen said:**
> There is no need to re-boot unless he has installed drivers (like nvidia or ATI).


There is a need to restart X, however.  And gdm does not always recover from ctrl-alt-backspace.

---

### Post by Speedycat on 2006-10-01
Okay seriously guys.

Yes I have edited my xorg.conf successfully to include my desired resolution.

In my monitor section, it only says this:

Section "Monitor"
	Identifier	"IBM E74"
	Option		"DPMS"
EndSection

So what should I do?

---

### Post by bodhi.zazen on 2006-10-01
> **Speedycat said:**
> In the first post I already said I edited xorg.conf :3

My monitor section is nearly empty with no refresh rate in the section, and I'm using an "Intel express chipset family 910" card.

Try installing the i910 driver:

[[color=blue]How to i910[/color]](http://ubuntuforums.org/showthread.php?t=259437)

I do not know a better link, sorry, but this one should do.

---

### Post by sbergman27 on 2006-10-01
> **Speedycat said:**
> My monitor section is nearly empty with no refresh rate in the section, and I'm using an "Intel express chipset family 910" card.

From the website:

Horizontal frequency (kHz): 30 to 69
Vertical frequency (Hz): 50 to 160

You might want to stay conservative, and use something like

HorizSync 30-67
VertRefresh 50-75

On second thought, since your monitor section does say E74, go ahead and put in the numbers from the website.  I think we can be pretty sure they are right.

---

### Post by bodhi.zazen on 2006-10-01
> **Speedycat said:**
> Okay seriously guys.

Yes I have edited my xorg.conf successfully to include my desired resolution.

In my monitor section, it only says this:

Section "Monitor"
	Identifier	"IBM E74"
	Option		"DPMS"
EndSection

So what should I do?

Look up....

You need to google your monitor and add the horizontal and vertical refresh rates as outlined in previous posts.

---

### Post by Speedycat on 2006-10-01
Okay, I'll let you know how it goes.
(ps, my video driver is fine, or else my max resolution would probably 640x480. It's obviously using it since openGL and 3D stuff works too)

---

### Post by bodhi.zazen on 2006-10-01
> **sbergman27 said:**
> 
Horizontal frequency (kHz): 30 to 69
Vertical frequency (Hz): 50 to 160

HorizSync 30-67
VertRefresh 50-75

You do not need to be so conservative with VertRefresh.

50-160 is fine if those are the correct settings for the monitor in question.

If you are guessing, you can break things....

Otherwise I'll leave it to you two.

---

### Post by sbergman27 on 2006-10-01
The monitor does not look quite the same as the one we found, but the model number is the same, and it did get picked up as an IBM E74, so I'd say we're probably safe to use the numbers from the site.

---

### Post by Speedycat on 2006-10-01
Okay, I changed the xorg.conf to look like this. I used the numbers from the IBM site, since I'm fairly sure it's the right monitor.

Section "Monitor"
	Identifier	"IBM E74"
	HorizSync 30-69
	VertRefresh 50-160
	Option		"DPMS"
EndSection

I just rebooted.

---

### Post by sbergman27 on 2006-10-01
In preferences->screen resolution do you see any new resolutions?

---

### Post by Speedycat on 2006-10-01
No, it still contains only 1024x768, 800x600, 640x480.

And refresh rate's only option is 85hz.

---

### Post by sbergman27 on 2006-10-01
OK.  In the device section, what is the "Driver" being used?

---

### Post by Speedycat on 2006-10-01
> **sbergman27 said:**
> OK.  In the device section, what is the "Driver" being used?

In xorg.conf or Device manager?

Video driver or monitor driver?

---

### Post by sbergman27 on 2006-10-01
In xorg.conf

Video driver.

---

### Post by Speedycat on 2006-10-01
Ah...

My driver is i810..

My device is actually an i910.

---

### Post by sbergman27 on 2006-10-01
I believe that is OK.  Look at bodhi.zazen's link about i910.  Get the i915 resolutions package mentioned in it, via synaptic.

---

### Post by bodhi.zazen on 2006-10-01
> **Speedycat said:**
> Ah...

My driver is i810..

My device is actually an i910.

Look up...... :lol:

---

### Post by Speedycat on 2006-10-01
Actually, I already installed 915resolution from synaptic o_o

Weird. I'll reinstall it.

---

### Post by sbergman27 on 2006-10-01
> **bodhi.zazen said:**
> Look up...... :lol:

If I'm reading this correctly, i910 needs some bios fiddling to do higher resoutions.  Is that correct?

And we'll need to configure the initscript to do it with each boot, right?

---

### Post by Speedycat on 2006-10-01
Well I've reinstalled 915resolution, but nothing happened. I'm going to reboot again and hope something does because this is a really annoying problem...

---

### Post by sbergman27 on 2006-10-01
Have a look at /usr/share/doc/915resolution/README.Debian

It explains how to use it.

---

### Post by Speedycat on 2006-10-01
When I type "915resolution -l" it says "operation not permitted, I/O permission" or something

---

### Post by sbergman27 on 2006-10-01
sudo 915resolution -l

---

### Post by Speedycat on 2006-10-01
Well I have to go now, I'll continue fixing it later.

Thank you SO much for all your help

---

### Post by sbergman27 on 2006-10-01
I think it will probably work.

And thanks Bodhi.zazen!  "Video Bios Needs To Be Fiddled With" was pretty far down on my troubleshooting checklist! ;-)

---

### Post by bodhi.zazen on 2006-10-02
> **Speedycat said:**
> Well I have to go now, I'll continue fixing it later.

Thank you SO much for all your help

Speedy: :lol: did you get up and running?

I posted a how-to here:

[bodhi's How-to](http://ubuntuforums.org/showthread.php?t=269052).

[list=number][*]First, I HTH.[*]Second, if you have any comments it would be helpful if you anwser this thread, PM myself, or reply in my how-to so as to help me help other new users such as yourself.[/list]

---

