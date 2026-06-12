---
title: "nitpicky complaining..."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-04
**1.**
hey, this is pretty perfectionist of me but, my menu looks like this:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-8.png[/IMG]

and you say, "so whats wrong?" Well, notice the Accessories, Graphics and Office Icons? They are blurry. Which is... annoying me :-/ I think the where clear to begin with, when I install Ubuntu, but no more..

**2.**
In Firefox:
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-9.png[/IMG]
can I change the button styles to something else? Is there a HowTo on how to do this somewhere?

Thanks so much!! :D

staticvoid

whoever can figure this out can eat my popcorn: :popcorn:

---

### Post by original_jamingrit on 2007-12-04
Hi,

As to your first question, I'm not using my ubuntu partition so I can't say for sure; but I'm pretty sure the icons should be rendered a bit more clearly than it seems in that screenshot.  You should search around the forums to see if anyone else has had problems with blurry svg icons.

As for the second question, there is a tutorial on how to get your firefox widgets to become similar to GNOME's.  Check out this tutorial [http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets](http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets) to see how.  I think you can also change it using a firefox plugin (In firefox, go to "Tools"-> "Addons", and then click the "Get Extensions" link.

---

### Post by staticvoid on 2007-12-04
Hey thanks, That tutorial worked great :)

now for the icons..

---

### Post by drted on 2007-12-04
Check out how to install the Tahoma font from this tutorial:
[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

8pt Tahoma makes everything look MUCH better (IMO night and day difference) than the default "Sans" font ubuntu uses.

But if you don't want to change the font you could just turn off antialiasing in Appearance -> Fonts

---

### Post by LowSky on 2007-12-04
are you using a LCD or CRT monitor? What is you video card?

---

### Post by FuturePilot on 2007-12-04
I think the icon issue has to do with the fact that they don't have a scalable svg for that icon so it's trying to enlarge a png icon which results in a fuzzy image.

---

### Post by staticvoid on 2007-12-04
Ok, cool. I've learned a lot.

I changed my font for applications to UnDotum. Thats why! :)

I have an LCD monitor.

anyway, i'll post what a tahoma 9 font did :)

be right back

s

---

### Post by staticvoid on 2007-12-04
well... it did not work... i've switched to the "mist" icon set... seems a little clearer.

sv

---

### Post by CatKiller on 2007-12-04
Those icons are theme-dependent.

If an icon of the right size is available in a theme, that icon gets used. If there is no icon of the right size, the SVG icon gets scaled. If there's no SVG icon, the bitmap icon at a different size gets scaled (which is what happened here). If there's no icon available at all in that theme, the theme that it depends on is checked, and so on all the way back to the hi-color theme, which is frankly quite challenging to look at.

So your options as I see them are[LIST=1]
[*]Find an icon theme that has icons that you like in the right size for the menu entries
[*]Find icons that you like from another theme or another source and insert them into your current theme
[*]Make new icons that you like
[*]Put up with it :)
[/LIST]

---

### Post by Ptero-4 on 2007-12-04
As for firefox. Install firefox 3. It draws the webpages buttons using your gnome theme.

EDIT: Mixed up the release's names. It's gutsy and hardy.

---

### Post by staticvoid on 2007-12-05
FF3 is out allready??

wow. i live under a rock

---

