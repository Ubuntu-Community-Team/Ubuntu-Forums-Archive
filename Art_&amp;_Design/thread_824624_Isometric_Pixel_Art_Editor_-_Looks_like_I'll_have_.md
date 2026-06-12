---
title: "Isometric Pixel Art Editor - Looks like I'll have to make one myself!"
date: 2008-06-10
forum: Art &amp; Design
---

### Post by lucasl on 2008-06-10
Hi,
I've looked for a decent raster editor for Linux (and Windows) to no avail.
GIMP is too bulky, ms/x/mt/tux/... paint all lack certain features that really help an aspiring pixel artist including zooming, transparency/layers, lines that show as they draw (GIMP shows it but not a pixel version) and basic transform.
Other isometric only features would be nice too, such as draw an isometric grid/square/circle (and possibly cube, sphere...)

One feature which I think would be especially handy is a colour picker that from one colour picks more, eg when it is in shadow, light, highlights, etc.

Anyway, my point is that this program doesn't exist (if it does, please share), so I'm going to foolishly attempt to make one myself. It'll probably go down the drain but I may as well try.

The question: what language/libraries should I use?
Keep in mind I am a rather inexperienced coder. I know a little c++ and python, but would prefer ruby. The only real GUI library I've used is WxRuby and WxPython, so using that (somehow) would be nice (although I doubt that would be possible). Or, I could learn to use Ruby/Gtk, but there doesn't seem to be an easy was to do raster editing?

Thanks!

Edit: Looks like Ruby/Gtk using a Gtk::DrawingArea canvas will be it, unless anyone has some suggestions.

---

### Post by h4ck3rc1 on 2009-02-14
i have been looking for a similar program for making an isometric floor plan, no luck yet either.

---

### Post by AJB2K3 on 2009-02-14
GIMP maybe too bulky but nothing allows yous to save frequently duplicated parts (windows, people, cars) as brushes.

---

### Post by m83 on 2009-02-14
You should try [mtPaint]("http://mtpaint.sourceforge.net/").

---

### Post by smartboyathome on 2009-02-14
> **m83 said:**
> You should try [mtPaint]("http://mtpaint.sourceforge.net/").

The OP said they did, and it lacked features. ;)

---

### Post by AJB2K3 on 2009-02-15
[IMG]http://i51.photobucket.com/albums/f352/AJB2K3/alpine.png[/IMG]
Was made in mspaint which has only basic editing tools.
What features do you want for pixel editing.
BTW it was made for pixeldam but I had it removed because I never finished it.

---

### Post by wjaguar on 2009-02-15
> **smartboyathome said:**
> The OP said they did, and it lacked features. ;)

More likely the OP lacked RTFM-fu. :-)

---

### Post by lucasl on 2009-02-16
> **wjaguar said:**
> More likely the OP lacked RTFM-fu. :-)
Sure, any paint program that can draw lines in different colours and zoom is sufficient, but what I wanted was one that makes life easy. Read the OP.
And I gave up on making one.:D Couldn't find a single relatively easy raster drawing library for linux. Tried using Cairo and making it act like a raster, but unsuprisingly it didn't work (blurry not pixelly and slow when zoomed in).

---

### Post by wjaguar on 2009-02-16
> **lucasl said:**
> Sure, any paint program that can draw lines in different colours and zoom is sufficient, but what I wanted was one that makes life easy. Read the OP.
It is precisely the OP that shows poor RTFM skills. Because all the _named_ features in there, mtPaint for one has since version 2.00 from 3+ years ago. Not noticing those same features in version 3.20 - *despite* the existence of an illustrated manual - must have taken some doing. ;-)

> **lucasl said:**
> And I gave up on making one.:D Couldn't find a single relatively easy raster drawing library for linux.
Actually, there exists **libmtpixel**, made for exactly this specific use. But what the need - when there already exists a number of open-source image editors just waiting to be improved? Open source allows one to build upon an existing foundation, instead of reinventing the wheel.
Or had *"submitting a patch"* and *"making a feature request"* both gone out of fashion recently? ;-)

---

### Post by lucasl on 2009-02-17
Hmmm... my bad, mtpaint does have all those features.

However, I find the interface clunky and dated. I especially can't stand the palette system (though I guess it is good for gifs and other palette based images). My own fault really.

I don't really have the knowhow to submit a patch (although I admit I haven't looked at the source), and a feature request isn't really relevant due isometric tools are too specific for a general painting program.

---

### Post by wjaguar on 2009-02-17
> **lucasl said:**
> However, I find the interface clunky and dated. I especially can't stand the palette system (though I guess it is good for gifs and other palette based images).
Images which are not palette based, are usually not considered to be pixel art.
And given the multitude of theme engines that exist for GTK+, interface beauty is entirely in user's hands. :-)

> **lucasl said:**
> feature request isn't really relevant due isometric tools are too specific for a general painting program.
mtPaint isn't "a general painting program" by any stretch of imagination. It is a pixel art editor with some general-purpose features, so this kind of niche tools likely would fit well to it.
And anyway, what harm could be in trying? A requested feature can get implemented, or at worst rejected - but a feature that was **not** requested, is "rejected" by definition.

---

### Post by AJB2K3 on 2009-02-17
Just a thought but have you tryed to hack the gimp?

A slimed down version would do perfect.

---

