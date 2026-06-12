---
title: "why kubuntu, why?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-19
I'm afraid my kubuntu experience up to now has been very frustrating indeed.  With the multiple issues I've experienced including screen freezes necessitating unplugging of my notebook battery (I've never had to do this before), I don't understand how kubuntu is said to be more stable and efficient than windows XP.

But onward I toil, hoping that all the effort will someday be worth it.  To that end, I hope someone can help me with these questions:

1) Is there some way to reboot my notebook when kubuntu freezes?  When it freezes, the power button doesn't work, the cdrom cannot open and alt-cntrl-del doesn't work.  Is there some other way?

2)  My problems originally began when I tried to fix the screen resolution (it was very 'pixelated').  I have a Via/S3 unichrome pro IGP chipset.  The vesa driver is chosen by default.  The maximum resolution available in system settings is 800x600.  On someone's advice, I ran dpkg-reconfigure xserver-xorg and selected the higher resolutions.  When I did that, the system would fail to boot and I'd end up at a text screen.  I've also tried editing the xconf file in kate but it says I need to be in "root".  Any other thoughts?

3) My broadband internet connection seems to be running at less than dial-up speeds.  I confirmed that it wasn't an ISP issue by trying it in windows

A note to the developers: 

I did a few years of programming as an undergrad student and that was tough, so I can't begin to imagine the complexities involved in creating an OS.  However, linux-based systems seem to be beyond the capabilites of the average user.  Most people need to point and click not type some obscure bit of code to get things working.  My humble suggestion is that this barrier to usability be afforded more focus in future versions.

Again, many thanks to you all for your efforts and patience in helping me.

Regards,
keno

---

### Post by wmblowers on 2007-11-19
I'm a relative newbie also, but I do have one suggestion which you may have already tried:  perhaps holding the power button down for at least several seconds will force a shutdown.  On my two desktops, if I need a forced shutdown I hold down the power button in until they die.

Good luck, and don't give up.  When it works, it's awesome!

WLB  :>)

---

### Post by PmDematagoda on 2007-11-19
> 1) Is there some way to reboot my notebook when kubuntu freezes? When it freezes, the power button doesn't work, the cdrom cannot open and alt-cntrl-del doesn't work. Is there some other way?


Yes, there is, press Alt+PrntScrn(Keep holding them through the rest of the sequence)+R+S+E+I+U+B(An easy way of remembering this is using the phrase "Raising Skinny Elephants Is Utterly Boring":). These key strokes safely unmount and disconnect all your hard drives and devices and restarts the system.

2) I do not know the answer as I don't have much experience concerning S3 VGA cards, sorry.

3) Not very sure about this one as well.

---

### Post by Sarteck on 2007-11-19
1) Well, I'm not sure if it would work (since it's frozen), but you could try CTRL + ALT + BACKSPACE.  This normally reboots the X Server (which is what gives us our GUI display instead of a console screen).  Alternatively, have you tried pressing and holding in the power button for 5 seconds?

Granted, this should not have to be done in the first place.

2) If you open up a Terminal (in Kubuntu, go to the K Menu, System, Konsole), type in **sudo nano /etc/X11/xorg.conf**, that should allow you to edit the Xorg configuration file.  However, I would advise against it if you don't know what you are doing, and if you decide to do it anyway, make sure to make a backup file!  You may want to see, though, if there is a specific configuration utility for your IGP chipset.

3)  What kind of speeds are we talking here, and how much of a difference is it?  Are we talking for uploading, downloading?  Both?  Is this regular browsing, or something like, say, torrents?

---

### Post by ugm6hr on 2007-11-19
> **keno.mentor said:**
> I've also tried editing the xconf file in kate but it says I need to be in "root".  Any other thoughts?


Not sure exactly what's going on with your system - but do have a couple of thoughts:
To edit files that need "root" - to this:
```
kdesu kate *filename*
```
This is explained on this website: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The other thing that might help people assist you is to give relevant hardware details: e.g. your network card / how you connect to the internet etc.

I would also recommend you use 2 separate threads for your problems.

As for rebooting - holding down the Power button (as suggested) for about 5 secs will generally hardware turn off (bypassing Kubuntu) - or try Ctrl-Alt-Backspace (instead of Ctrl-Alt-Del), which restarts X (i.e. graphical interface), which is generally the issue rather than Linux itself.

Hope some of that is helpful.

---

### Post by jaybombalous on 2007-11-19
> 
I did a few years of programming as an undergrad student and that was tough, so I can't begin to imagine the complexities involved in creating an OS. However, linux-based systems seem to be beyond the capabilites of the average user. Most people need to point and click not type some obscure bit of code to get things working. My humble suggestion is that this barrier to usability be afforded more focus in future versions.

firstly, u will get no sympathy from me. Linux is easier then windows ever thought of being, you just gotta stop thinking like a windows user while using a lunix OS. Yes, its that simple. Point and click is so... yesterday... its not even kewl anymore.

I don't know what resolutions u tried, but if the chipset is that old then the resolution can't be over 1024x768. Maybe even 800x600. On laptops, resolutions are different. A 800x600 resolution on a 1024x768 laptop screen will not just give u bigger desktop objects, instead u will get a 800x600 window inside of the 1024x768 lcd display.

With that said, xorg will always try to use the highest resolution in xorg.conf. So u must go in here and remove any mention of a higher resolution then the highest setting on your laptop. Check the documentation instead of blindly guessing next time.

---

### Post by Sarteck on 2007-11-19
jaybomb, I have to disagree with just about everything you've said.  Heh.

"Point and click" is the VAST majority of what I and my family do in Linux.  To say that "Point & Click"ers are restricted to Windows and to demean it like you do is so... yesterday.

Also, his chipset is hardly what one would call "that old."

Finally, you're suggesting to someone who is obviously new to Linux to modify his/her xorg.conf?  I'm still a newbie, I admit, but I've been around a bit in there, and when there are like fourteen different parts that I'd have to edit for a line defining a new resolution mode, I'd rather have it done FOR me, instead of me doing it by hand.



To the original poster:  ugm6hr's suggestion of using kdesu is better than mine of using nano, actually.  Check out the link s/he posted, too, if you want to gain an understanding of running things as root.

---

### Post by Paradoxfox93 on 2007-11-19
> 
A note to the developers:

I did a few years of programming as an undergrad student and that was tough, so I can't begin to imagine the complexities involved in creating an OS. However, linux-based systems seem to be beyond the capabilites of the average user. Most people need to point and click not type some obscure bit of code to get things working. My humble suggestion is that this barrier to usability be afforded more focus in future versions.

> **jaybombalous said:**
> firstly, u will get no sympathy from me. Linux is easier then windows ever thought of being, you just gotta stop thinking like a windows user while using a lunix OS. Yes, its that simple. </b>Point and click is so... yesterday... its not even kewl anymore.
.</b>

HAHAHA!!!!!  That's rich.  Seriously though. Getting off microsoft is like getting off crack the NA way...Just for today...
I don't have anything helpful to contribute to the the thread.  But I feel like I need to say that learning all the code is certainly worth getting off microcrack.  Don't get me wrong, Ubuntu is taking a huge crap on my MT3422 with a very small light at the end of the tunnel that really looks like shelling out another $100 to buy USB sound & wireless. :-/ Still A deaf, dumb, and wired computer is better than getting smoked by microcrack.

And no...I'm not dual booting...I'm goin' cold turkey, man...

---

### Post by keno.mentor on 2007-11-20
Thanks for the comments guys.

I was just giving my personal experience so far.  I didn't mean to suggest that windows was superior to a  linux-based OS.  Indeed, I am labouring on because my research tells me that, once it works, linux is the better OS. 

My chipset is not that old, as far as I know.  Also, I know that the resolution I need is 1280x800 at 60Hz.  My problem is where do I specify this?  When I run kdesu kate /etc/X11/xorg.conf a window pops up with xorg.conf listed in the left panel but no other text anywhere else

Yes, I am a microcracker trying to get through rehab.  But admitting I have a problem is half the battle won, right? :) Thanks to those who reply with patience and understanding

Regards,
keno

---

### Post by bruce2000 on 2007-11-20
> **keno.mentor said:**
> 
2)  My problems originally began when I tried to fix the screen resolution (it was very 'pixelated').  I have a Via/S3 unichrome pro IGP chipset.  The vesa driver is chosen by default.  The maximum resolution available in system settings is 800x600.  On someone's advice, I ran dpkg-reconfigure xserver-xorg and selected the higher resolutions.  When I did that, the system would fail to boot and I'd end up at a text screen.  I've also tried editing the xconf file in kate but it says I need to be in "root".  Any other thoughts?


I have the same graphics chipset, built into the motherboard. I don't know if this will work for you, but it allowed me to change the res. from 800x600 to 1280x1024:

```

sudo dpkg-reconfigure -phigh xserver-xorg

``` 

And choosing "vesa" from the list. (I know you've tried something similiar already; this method just chooses the video driver, and avoids all the other options)

It's worth making a backup of xorg.conf in case something goes wrong:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup

```

---

### Post by Skip Da Shu on 2007-11-20
> **keno.mentor said:**
> Thanks for the comments guys.

I was just giving my personal experience so far.  I didn't mean to suggest that windows was superior to a  linux-based OS.  Indeed, I am labouring on because my research tells me that, once it works, linux is the better OS. 

My chipset is not that old, as far as I know.  Also, I know that the resolution I need is 1280x800 at 60Hz.  My problem is where do I specify this?  When I run kdesu kate /etc/X11/xorg.conf a window pops up with xorg.conf listed in the left panel but no other text anywhere else

Yes, I am a microcracker trying to get through rehab.  But admitting I have a problem is half the battle won, right? :) Thanks to those who reply with patience and understanding

Regards,
keno 
I'm also going cold turky off of MS and I think both u and I have not chosen the easiest path.  You with Kubuntu and me with Xubuntu.  It seems from what I've been reading and what I've seen the Gnome version, regular Ubuntu is easier especially in the "do it from the desktop" department.

---

### Post by keno.mentor on 2007-11-21
I tried that but it only lets me select the driver (vesa in this case).  It closes down and takes me back to the terminal window without allowing me to specify the resolution.

Please help,
keno

---

