---
title: "Any have an Icc Profile for a iBook?"
date: 2008-02-28
forum: Apple PPC Users
---

### Post by Gen2ly on 2008-02-28
Hello all.

I just got thorough alot of the details of configuring up my iBook and now that I'm fairly comfortable with it I'd like to be able do something about the color.  Its not something thats too bad, but I have been beginning to notice that artwork I do looks different on other computers.  This is a bit of an issue cause I no longer have OS 9.  

I have learned that LProf has the ability to calibrate the display but it needs qt and I can't really spare the disk-space.  Anybody have an Icc profile about and mind sharing, I'd be very very thankful.

---

### Post by stream303 on 2008-02-28
Now that would be a great find.  When I was doing some work in Gimp, the closest I could get was to try and match my gamma the best I could by eyeball with some gamma charts, and using xgamma at the commandline, ie:

```
xgamma -gamma 0.8
```

An icc profile would definitely rock!  Sometimes I use this as a fake brightness control, since my machine doesn't have any way to adjust it.

---

### Post by Gen2ly on 2008-02-28
Thanks stream303 this definitely gets me going.  I'm play about with LProf today I'll give a report on how it goes. 

The brightness or gamma?  The brightness can be adjusted using fblevel.  Valid values for to this iBook are 0-16.  Its in the powerpc-utils in Gentoo.

---

### Post by stream303 on 2008-02-28
Unfortunately fblevel doesn't work on my G5 iMac with nvidia card, but hopefully should on most notebooks.

As for gamma, I used the charts and info from here:

[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)

Once you've found the right gamma setting with xgamma, you can make it permanent by adding it to your monitor section of xorg.conf.  Mine looks like this:

(I just called up the page and a small terminal, and changed it with xgamma -gamma 0.5 or 0.75 or 1.0 or 1.2 etc and eyeballed the changes.)

```
Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
	**Gamma		0.8**
EndSection
```

This is all just by eyeballing it, so it is very subjective - I wouldn't go editing images that my career depended on unless I could calibrate it. :)

This could probably be a big help for aging crt's on the imacs though.

The biggest help for me when I was using external monitors that had their own internal adjustments, was to make sure that I started out correctly with a temperature of 6500k.  Easy to forget when you have the monitor in some other preset like "media, gaming, text, web" etc.  Get that initial color temp right and go from there.

I also used that page to confirm what my eyes were seeing on my 1680x1050 iMac screen - I changed the font dpi to 105, and the chart showed that for my resolution 101 was the best bet.  I just went into the font prefs (or appearance on Gutsy), chose the "detail" tab, and was then able to change my dpi accordingly.  Nice.  This will differ depending on your own screen resolution obviously.


But now we're getting way out from ppc specific problems. :)

---

### Post by Gen2ly on 2008-02-29
This is definitely getting my attention.  Pretty cool.  First, have to say that I didn't have any luck trying Lprof today.  I was able to get in installed and tried a very basic calibration.  Was able to get it to save finally:

```
touch ibookprofile.icc
```

select that file in the diallog button "..."
and finally "Save to Profile"

Unfortunately either how Lprof saves to file or how xcalib reads the file aren't compatible (although I read that not all videocards are able take a couple settings.  There's ArgyllCMS but from what I understand it's capability is to record information from a spectrophotometer or colorimeter so possibly no hand configuration.  It does have a program that can apply an icc profile though so maybe I'll give it a try.

As for xgamma it does help.  Mac displays must be hardware calibrated to 1.8 gamma because my MacBook was exactly the same - too bright in Linux.  I know that sounds funny but setting the gamma as 2.2 in Mac OS 9 or X is about the same as setting xgamma to .8 - its how it is though.

Good to hear about the xorg.conf tip - very very handy.  

The page on calibration is a pretty good explanation too.  Though I like to be able to use OS X's Colorsync - its really good.  Its able to do color adjustments on several different levels.  I put a color scale in the background

[http://www.tranquilityimages.com/calibrate.shtml](http://www.tranquilityimages.com/calibrate.shtml)

and I find I am able to notice color discrepancies in the gray very very easy.  Unfortunately thats another topic too.

As for the DPI, I'm not sure I would alter it.  Xorg 7.3 now calculates and uses the value that best for the lcd, and I'm pretty sure Gnome uses that value.  To find what the native dpi is for the resolution:

```
cat /var/log/Xorg.0.log | grep DPI
```

Mine is:

```
(==) MACH64(0): DPI set to (75, 75)
```

As Gnome takes this value and calculates the algorithm for font aliasing.

If anybody has an iBook profile about (icc profile) I'd like to try it. :) :) :)

---

### Post by stream303 on 2008-02-29
> **Dirk.R.Gently said:**
> As for the DPI, I'm not sure I would alter it.  Xorg 7.3 now calculates and uses the value that best for the lcd, and I'm pretty sure Gnome uses that value.  To find what the native dpi is for the resolution:

```
cat /var/log/Xorg.0.log | grep DPI
```

Mine is:

```
(==) MACH64(0): DPI set to (75, 75)
```

As Gnome takes this value and calculates the algorithm for font aliasing.

OMG!!  All this time I thought it was just a manual preference kind of thing.  Unfortunately, 75 dpi seems like the fallback position that is used when it can't determine the right one.  The original Mac in the 80's had 72 dpi, and even Windows uses 96 by default.

This issue is large enough that I'm going to start a new thread to get more exposure since I believe that many of us might be using the safe fallback without knowing it.

---

### Post by Gen2ly on 2008-02-29
> **stream303 said:**
> OMG!!  All this time I thought it was just a manual preference kind of thing.  Unfortunately, 75 dpi seems like the fallback position that is used when it can't determine the right one.  The original Mac in the 80's had 72 dpi, and even Windows uses 96 by default.

This issue is large enough that I'm going to start a new thread to get more exposure since I believe that many of us might be using the safe fallback without knowing it.

Definitely good to know.  In my head I figured that 75 is about right but its not.

```
echo 'scale=5;sqrt(800^2+600^2)/12.1' | bc
```

I just read the specs and it's 85 DPI.  I've wrote about this before:

[http://linuxtidbits.wordpress.com/2007/08/08/fonts-and-dpi/](http://linuxtidbits.wordpress.com/2007/08/08/fonts-and-dpi/)

doh!

---

### Post by stream303 on 2008-03-01
Looks like for total reliablility, it is best to just calculate it yourself like you did.

sqrt (horiz pixels ^2 + vert pixels ^2) / diagonal inches

I found some nifty additional info from Mozilla, which was great for manually setting my dpi on very minimal systems with nothing more than just a simple window manager:

[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

Running nothing more than twm window manager on a G5 with 1.5 gb of memory is kind of a crackup.  Sure is fast though... :)

---

