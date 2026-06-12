---
title: "[SOLVED] WTF? ImageMagick &amp;quot;composite&amp;quot; not working"
date: 2007-11-10
forum: Art &amp; Design
---

### Post by Old *ix Geek on 2007-11-10
Maybe it's just too early in the morning and/or I've had too little coffee, but I'm absolutely stumped. :confused:

I've used this command hundreds of times before: ```
composite -gravity center image1.jpg original/thumbnail_150x150.jpg image1_revised.jpg
``` to overlay and center "image1.jpg" (which is 135x135 pixels) on top of "thumbnail_150x150.jpg" (which is 150x150 pixels and located in the "original" directory).  Note that the two images I'm attempting to combine are each RGB, true color, 300x300 dpi, 1 layer.

Instead of doing what I described, it's creating "image1_revised.jpg" as grayscale, true color, 300x300 dpi, 1 layer, and WITHOUT any sign of "image1.jpg" overlaid on it.  Like I said, I'm stumped.  I even went to ImageMagick's site and verified my syntax against [their example](http://www.imagemagick.org/script/composite.php): ```
composite -gravity center smile.gif  rose: rose-over.png
``` and don't see anything wrong with mine.

Thoughts? Suggestions? Other info from me that might be helpful?  Let me know!

---

### Post by geirha on 2007-11-11
I tried downloading smile.gif and rose.jpg from that page and copy/pasted the command. It didn't work either. It only showed the rose. Looks like a bug to me.

---

### Post by Old *ix Geek on 2007-11-11
But the thing is, I've done this a zillion times before.  I can't think of anything I've done/changed that could explain this sudden failure. :confused:

---

### Post by newOldUser on 2007-11-12
I just tried this myself and it does not seem to be working.  
composite -verbose -gravity NorthWest cropWeather.gif current.jpg Hamtest.jpg

I'm using ubuntu 7.10 server install with a xubunu desktop. I know this command works on other distros of linux but I've never tried it on this machine till now. 

composite -version command shows: 
Version: ImageMagick 6.2.4 10/02/07 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)

uname -a shows:
Linux uServer 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I also tired using the geometry option and it did not work
 composite -verbose -geometry +15+30 cropWeather.gif current.jpg Hamtest.jpg

Please post if you find a fix, I'll do the same

---

### Post by Old *ix Geek on 2007-11-12
Here's my output for **composite -version**:

Version: ImageMagick 6.2.4 10/02/07 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2005 ImageMagick Studio LLC

and for **uname -a** on the laptop I'm on right now (but I've also tried this on two other Feisty boxes, with the same result):

Linux HPLaptop 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

I see we have the same version/date of ImageMagick.

I used to use this command extensively on a Ubuntu 5.04 box (which I FINALLY wiped recently and clean-installed Feisty), and now I'm wondering if something's changed in IM since whatever version I was using before.  Now that I think about it, I can't recall trying it on any of my Feisty boxes until now...damn, I wish I hadn't wiped Hoary!  I'd like to try it there and see which version of IM was on it (I almost NEVER updated anything on that box, so the odds are very good that it was a much older version of IM).

Should I/we bug report this?

---

### Post by newOldUser on 2007-11-12
I have an older version of DamnSmallLinux that has the imageMagick tools. The composite function works fine 

The ImageMagick version is 6.2.4 08/16/05 Q16 
The kernal is 2.4.26

I did a little hunting around with google but wasn't able to find anything. I'd say go ahead and send in a bug report.  The question is, do you send it to ubuntu or imageMagick

---

### Post by Old *ix Geek on 2007-11-12
Okay, my problem is solved--but only because I changed to a different version of ImageMagick.  Here's my info now:

Version: ImageMagick 6.3.6 11/12/07 Q16 [http://www.imagemagick.org](http://www.imagemagick.org)
Copyright: Copyright (C) 1999-2007 ImageMagick Studio LLC

Now my much-needed **composite** command is back to working like a charm. :D

I'm not going to bother bugging this issue because there are newer versions of IM available, so, apparently, the bug was already reported and fixed.

---

### Post by newOldUser on 2007-11-15
Hey that's great.  Where did you get the new package from?

---

