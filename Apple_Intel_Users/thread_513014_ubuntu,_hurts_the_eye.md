---
title: "ubuntu, hurts the eye"
date: 2007-07-30
forum: Apple Intel Users
---

### Post by anujseth on 2007-07-30
I have this problem with ubuntu it seems to be really stressful to the eyes, i mean i sit and read for long durations(ebooks etc) and doing this really starts hurting the eyes etc. its not ubuntu's fault i ve been using it for a couple of years now and never had this problem before on my dell machines ... its just that it doesnt feel right on the macbook. i had posted the color correction thing earlier but this also makes only a minor difference.

is it because of the widescreen ?? i mean even win xp hurts the eye on this macbook ... OS X has no such problems ... ubuntu in VMWare Fusion is infinitely better infact its perfect except for the black borders around the screen. Infact i was wondering whether this is actually to do with the 1280x800 resolution cause VMWare feels fine and thats 1024x768 ... all of my previous machines where also of similar resolutions. maybe ubuntu is not cut out for the widescreen or atleast 915resolution and the xcalib gamma fix are not the right way to go about it. increasing decreasing contrasts makes not difference it always feels as if something is a bit out of focus if you know what i mean.

---

### Post by ronocdh on 2007-07-30
I have encountered no such issues. In fact, on my 15" glossy screen, I feel like Ubuntu is actually more vibrant and crisp than OS X, and that's saying a lot. I recommend checking out font solutions to increase readability, if you're experiencing eye fatigue.

I agree that WinXP looks ugly as sin, even on a Mac. ;)

---

### Post by anujseth on 2007-07-30
:( ... i miss my dell (thats prolly the hundreth time i ve said this to someone or posted it somewhere) ... 
 can u elaborate a bit on the font issue ... i usually have the msttcorefonts installed ... however with and without it things are the same ... and the gutsy tribe 3 defaults are hideous ... beryl does make it look a bit snappier but it breaks madwifi qutie often and kills netbeans ...

---

### Post by Gen2ly on 2007-07-30
It did mine too before using and icc color profile.  I also tend to use darker-themes.  Also speaking of which are the best fonts, rono could be right that this may be a font issue.  To use with a browser microsoft fonts aren't that tailored to Linux so you could find possibly some better ones out there.  Here's a screenie of the browser I'm using:

---

### Post by anujseth on 2007-07-30
yeah that seems to be the ubuntu studio theme ... it definitely makes things better ... but still does not fix the problem  ... post screenshots of ur font configs if possible ... 

also gutsy tribe 3 detects 1280x800 out of the box but the fonts on that atleast for me are horrible sans set to 11 ... now these very settings look awesome in VMWare but on a native install they look just appaling even after the icc profile ... PS im attaching my icc profile below .. use it and compare to urs 

also does anyone know how to keep the fans upto 3000 or whatever in gutsy ... without having to use smc fan ctrl in os x first and then rebooting

---

### Post by anujseth on 2007-07-30
heres another insteresting thing ... OS X settings put the display at 1280x800 and the refresh rate is O Hz and is blacked out as in cannot be set ... VMWare the one that makes the display look good in ubuntu also sets it at 0 Hz .... ubuntu native sets the refresh rate to 60 Hz with no option to change it. could it be ...

---

### Post by russo.mic on 2007-07-30
Well, I don't think the refresh rate is really 0 Hz, as it would never refresh, as 0 Hz being nothing, and the screen would essentially be frozen with the last thing displayed on it, or would it be black...hmmmm...wrap your head around that.  

I've got the 15 inch C2D with the matte screen, and I think Ubuntu looks great.  I even think it manages to make Windows XP a bit less horrible looking...

Hmmm....there's always vista....


(kidding)

---

### Post by luisbg on 2007-07-30
it's not the ubuntu studio theme but it looks similar. the ubuntu studio theme can be easily installed through apt / synaptic, give it a try.

luisbg

---

### Post by Gen2ly on 2007-07-30
Linux desktop's are possibly designed with the Windows set of mind.

---

### Post by cyberdork33 on 2007-07-30
> **russo.mic said:**
> Well, I don't think the refresh rate is really 0 Hz, as it would never refresh, as 0 Hz being nothing, and the screen would essentially be frozen with the last thing displayed on it, or would it be black...hmmmm...wrap your head around that.

Yea, I believe the VM uses the refresh rate of the host OS (since having the two at different frequencies would make things very interesting, or even at the same frequency, but different ends of the cycle, etc) As far as the 60Hz rate, this is pretty much standard for LCD screens.

Have you changed the font settings to use subpixel smoothing for LCD screens?

---

### Post by anujseth on 2007-07-30
well OS X also shows n/a, XP 85Hz ... so it was just a thought

done the smooth pixel shading already

in general follow these for my installs - 
[http://ubuntuforums.org/showthread.php?t=452262](http://ubuntuforums.org/showthread.php?t=452262)
[http://ubuntuforums.org/showthread.php?t=491138](http://ubuntuforums.org/showthread.php?t=491138)
[http://ubuntuforums.org/showthread.php?t=501113](http://ubuntuforums.org/showthread.php?t=501113)

---

### Post by Gen2ly on 2007-07-30
I was talking about gamma

---

### Post by anujseth on 2007-07-31
installed gutsy tribe 3 again ... after changing the default font settings it is infinitely better ...  compiz and nautilus keep crashing however ...

---

### Post by cyberdork33 on 2007-07-31
> **anujseth said:**
> installed gutsy tribe 3 again ... after changing the default font settings it is infinitely better ...  compiz and nautilus keep crashing however ...

there are several bug reports on the two. also notification-daemon, gnome-power-applet, xorg, etc, etc, etc. Welcome to an alpha release of an OS.

---

### Post by cyberdork33 on 2007-08-22
Found this thread which might help the situation. Seems to look much better for me.
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

