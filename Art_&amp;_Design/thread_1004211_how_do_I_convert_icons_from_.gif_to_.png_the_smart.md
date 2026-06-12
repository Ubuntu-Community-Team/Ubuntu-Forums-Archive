---
title: "how do I convert icons from .gif to .png the smart way?"
date: 2008-12-07
forum: Art &amp; Design
---

### Post by amlucent23 on 2008-12-07
Can some gimp/inkscape savvy graphics pro help we with a problem, how can I convert a .png icon to a .gif icon without loss of quality (at least not too much)? And what program/settings would you recommend I use to do this? Also I should mention that the png icons I am converting contain transparency :(. I realize I need to crop it off or something as .gif doesnt do transparency.
[B]
My problem is that when I attempt in gimp the end result looks very crappy.[/B] I can post some examples if needed.

As you may have guessed I am a complete grphx noob.  Until recently I had never built a website or used gimp for that matter but I started a forum. I thought that the default icons that came with the software were ugly, so realized I could just use the tango icons that are gpl.. but they were in .png.  Then I had the breakthrough that I could just rename the .png icons to .gif and it worked.. but now they look ugly in IE6 and people are complaining. :oops:

---

### Post by smartboyathome on 2008-12-07
Just block IE6? Seems easier. ;)

Anyway, there's really no way to avoid GIF's uglyness. You're stuck I guess. :(

---

### Post by amlucent23 on 2008-12-07
well.. the main problem is the part of the png that should be transparent.. it shows up as white in IE6... which stands out on any background thats not white. Do you think that if I were to crop out the transparency of these images it would work?

---

### Post by twright on 2008-12-07
Just add a layer the background colour you require. Colours->Posterise should work to reduce the no. of colours.
I'm sure you could find an existing tango theme somewhere (i think this forum uses one).

---

### Post by -yay- on 2008-12-07
wouldn't it be better to convert them to jpg? That should give better color quality.

jpg doesn't support transparency either though, but you can just color the transparent areas the same color as the background on your website.

If that doesn't look good you can insert conditional statements in your code so that IE6 users are served different images than other users. (in other words you can give jpgs or gifs to IE6 users, and png to everyone else).

---

### Post by turezky on 2008-12-07
Your problem is a very common one ;) (Thanks to M$ and it's compliance with the standarts)
And you actually don't need any conversion... The result is always waaay to worse than if you'd use original PNG.
There's a hack that lets you use the PNG transparency with IE6!
Get the file from:
[http://www.twinhelix.com/test/iepngfix.zip](http://www.twinhelix.com/test/iepngfix.zip)
and just follow the tutorial inside.
You will need some basic knowledge of CSS.
For the most part it's quite self-explanatory example.

---

