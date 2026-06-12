---
title: "PANIC - Can get back to the graphics drivers I was using?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-03-02
Ok, will keep this simple (even if it's hard to understand!)

EDIT: Sorry, it's a long one as I needed to explain everything:

AMD64 3200+ CPU with ATI X800pro graphics and 1GB Ram

Going back 3 weeks..................................


Installed Ubuntu 7.1 a-fresh, upon bootup chose the restricted driver popup message and rebooted. After approx 1/2 a hour green interference/snow on screen which does seem with graphics card being over driven and over heating.

Installed Ubuntu a second time (told it to re-partition and format disk) this time did not select the popup message about restricted drivers, but instead installed ENVY to download ATI drivers. Again, same thing happened, so had to turn off PC.

Installed Ubuntu a THIRD time, Again, partitioned and formatted disk during install form the CD, and this time chose nothing. Did not install ANY ATI drivers.

But amazingly It all seemed smooth, was even able to select Advanced Visual Effects and Compiz Fusion all ran smooth as silk !!!

YES.

(Whilst this was fantastic, I assumed at the back of my mind I was not running REAL fast drivers and had never tried a game or anything) Even though all the 3D screensavers ran smooth.


Move forward 3 weeks to last night:

Installed Google Earth, and it was as slow and choppy as hell.
Ah Ha, I thought, This is the 1st prog that NEEDS full drivers.

So, I use ENVY to manually install ATI drivers v8.40.4
They install OK, but I can't select any "Advanced Desktop Features - Compiz" and Google earth did not run.

So, then used ENVY to get the latest ATI drivers, 8.01-86.86_64.RUN

They installed fine, I could turn Desktop effects on, and Compiz Ran.

But after 1/2 hour I had the green noise/pixel interference I had 3 weeks ago, and had to uninstall them.

I then rebooted and installed the "normal?" restricted drivers from the SYSTEM / ADMINISTRATION menu, these also gave me the green noise/pixels on screen after approx 1/2 of use, so I have to disable these.

Now..................

I appear to be just running the "FGLRX" driver, and graphic performance is horrid. Even moving just a window around screen is choppy, and no chance of any desktop effects.

So, I now eant to get back to what I was using last night before I started doing this messing about.

But, I've no idea what it WAS using.

If you recall back at the start, I did THREE Ubuntu installs.
The 1st time I selected "Restricted Driver" from Ubuntu's Bootup.
The 2nd install I used ENVY to get ATI driver.
The 3rd time I selected Nothing, and all ran smooth.

But I did tel Ubuntu to repartition the drive and it (said it was formatting partition) each time, so I can't see how anything would have been left behind after the 1st two installs to make the 3rd install work well. that's not possible is it?

I do have a backup of the XORG.CONF file in the X11 folder.


One from 16th Feb (I guess when I 1st installed Ubuntu) says:
[COLOR="Blue"]
Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/COLOR]

One from last night at 11:50pm (I guess before I started installing) says:

[COLOR="Blue"]Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/COLOR]

One 15 mins later (I guess after installing the new drivers)

[COLOR="Blue"]Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection[/COLOR]

And my current one (which was 1.5 hours after that)

[COLOR="Blue"]Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"vesa"
	Busid		"PCI:1:0:0"
EndSection[/COLOR]




Now, to my mind, it looks like the two early ones that read:

[COLOR="Blue"]Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/COLOR]

Are the ones I want to go back to. As it was working in Feb, and It seems it was the 1st backup file to be created when I started installing last night, so LOGICALLY they must be the working ones.

But, on the line [COLOR="Blue"]DRIVER[/COLOR] it just says [COLOR="Blue"]"ati"[/COLOR]

I'm wondering if I rename one of these old files to the current XORG.CONF what's it going to do/look for when it hits this "ati" line?

As since then I have installed and uninstalled drivers.

Do I assume this "ati" driver is something different and it will still be there, undamaged?

Any thoughts?

---

### Post by spiderbatdad on 2008-03-02
To have your graphics card reconfigured to the state it would have been, at the time of a os installation: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by djbsteart1 on 2008-03-02
I had a similer problem with installing/unimstalling drivers for my nvidia card. Luckily for you, you had the sense to make backups,I didnt and just reinstalled. 
I doubt that there is anything 'gifferent' aboutthe driver, but how Ubuntu 'uses' it is where the difference is. There will be nothing left on your hard disk from the first 2 installs if they were formatted. 

As it stands. it seems like the only option you have is to revert to the back up, and see if it works. You could also try, 
```
sudo dpkg-reconfigure xserver-xorg
```

That lets you reconfigure the xserver, and there is a chance that there might be something wrong, check the resolution and frequency that if is driving your screen at. If the frequency is too high there is a chance that the screen will be overloaded. Also a resolution that is too high could have smiler effects. 
But make a backup first, I assume you know how to do this as you have done it already.

I hope this helps in some way. Donald.

---

### Post by PiggiePaul on 2008-03-02
> **spiderbatdad said:**
> To have your graphics card reconfigured to the state it would have been, at the time of a os installation: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks for that.

I just used the command you posted and checked back at that file and now it says:

[COLOR="Blue"]Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/COLOR]

Which was the version I was thinking must have been the working one.

Rebooted and My smooth desktop is back and Advanced Effects (Compiz) is working again.

It's too early to say if this is a winner as it's not until about half a hour that I normally get the green sparkly/noise/interference pixels that I get with the "Proper" drivers.

I have everything crossed here, and I'm going to owe you a MASSIVE THANKYOU if It's fine now.

---

### Post by PiggiePaul on 2008-03-02
> **djbsteart1 said:**
> I had a similer problem with installing/unimstalling drivers for my nvidia card. Luckily for you, you had the sense to make backups,I didnt and just reinstalled. 
I doubt that there is anything 'gifferent' aboutthe driver, but how Ubuntu 'uses' it is where the difference is. There will be nothing left on your hard disk from the first 2 installs if they were formatted. 

As it stands. it seems like the only option you have is to revert to the back up, and see if it works. You could also try, 
```
sudo dpkg-reconfigure xserver-xorg
```

That lets you reconfigure the xserver, and there is a chance that there might be something wrong, check the resolution and frequency that if is driving your screen at. If the frequency is too high there is a chance that the screen will be overloaded. Also a resolution that is too high could have smiler effects. 
But make a backup first, I assume you know how to do this as you have done it already.

I hope this helps in some way. Donald.

Many thanks for the posting:

I actually used the:

[COLOR="Blue"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR]

command posted just before your's (albeit they look almost the same)

Must admit, I don't understand what they are doing, and what the difference between the two lines are?

But, so far so good (fingers and everything else crossed!)

Oh, and I don't really deserve the credit for backing up those files.
I'd like to say yes, I did that just in case, but in all honestly they were created automatically when the files were changed, and it's only today that I noticed there were backups !!!!!

---

### Post by djbsteart1 on 2008-03-02
Well I hope it keeps going well. I dont know the differnce either, but obviously both work. That probably means I had back ups as well. Dam. 
Enjoy a green free monitor.

---

### Post by PiggiePaul on 2008-03-02
Just an update:

YES......... It's still working.

Many MANY thanks to both of you for your help and getting me back to a system that works.

I'd like to ask, What does that command actually do?

[COLOR="Blue"]sudo dpkg-reconfigure -phigh xserver-xorg[/COLOR]

With (or without) the -phigh bit in there (whatever that does as well?)

I know I could have simply just edited my XORG.CONF file back to a version I thought was a working one.

But I don't know if that would have worked? (probably not)

I find it amazing that just 1 command line can undo all my graphics problems and out me back. I'd like to understand what the line/commands does?

---

### Post by djbsteart1 on 2008-03-02
I wish i could help on that, i am still at the very beginning of learning commands. From using it it seems to just give a more user friendly and graphical way of editing the XORG.CONF file. Other than that, all I can advise on is some basic commands for apt-get. 
You could try the wiki, or google.

---

