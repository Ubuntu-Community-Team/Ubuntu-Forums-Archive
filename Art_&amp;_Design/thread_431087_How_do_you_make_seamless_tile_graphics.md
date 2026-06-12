---
title: "How do you make seamless tile graphics?"
date: 2007-05-02
forum: Art &amp; Design
---

### Post by zami on 2007-05-02
I'm familiar with GIMP, but I'm wondering... is there a tiled preview mode I am missing somewhere?  Making seamless images seems incredibly tedious with GIMP.  Open image, edit, close, view in browser, see where I "missed", close browser, open image, try again, rinse, repeat... 

Is there something I'm missing?  Am I complicating this, or is it really this contrived to make a seamless image in GIMP?

I used to use Micrografx Picture Publisher, which had a great "tiled preview" mode.  The entire sizable window would be filled with repeats of the image you were working on - that is, just like a browser would display a tiling background image.  

The easiest way to make a seamless image in that program was to have your tiled preview open, and your working image open, and use a clone brush (or whatever fit the situation) on your working image.  You could see as you went along whether or not your sides were matching up.  Easy smeasy.

I miss it!

Again I plead, is there some feature I'm missing in GIMP?  Should I be using some other program for seamless tiles?

Thanks!

-zami

---

### Post by factotum218 on 2007-05-03
No that the linux community is growing in leaps and bounds maybe the shortage of application documentation will start to grow.
In the past I have found simple adobe photoshop tutorials (back around photoshop 7 i think) that worked well. You will have to interpret the steps to GIMP, but from what i remember it was quite easy. If i find anything usefull I will post it here.

---

### Post by ComplexNumber on 2007-05-03
> **zami said:**
> I'm familiar with GIMP, but I'm wondering... is there a tiled preview mode I am missing somewhere?  Making seamless images seems incredibly tedious with GIMP.  Open image, edit, close, view in browser, see where I "missed", close browser, open image, try again, rinse, repeat... 

Is there something I'm missing?  Am I complicating this, or is it really this contrived to make a seamless image in GIMP?

I used to use Micrografx Picture Publisher, which had a great "tiled preview" mode.  The entire sizable window would be filled with repeats of the image you were working on - that is, just like a browser would display a tiling background image.  

The easiest way to make a seamless image in that program was to have your tiled preview open, and your working image open, and use a clone brush (or whatever fit the situation) on your working image.  You could see as you went along whether or not your sides were matching up.  Easy smeasy.

I miss it!

Again I plead, is there some feature I'm missing in GIMP?  Should I be using some other program for seamless tiles?

Thanks!

-zami
i'm making tileable graphics at this moment. load an image into gimp that you want to make tileable. go to filters -> map -> make seemless. to preview the tiled image, go to filters -> map -tile, then increase the number by about 5 times or so.

---

### Post by zami on 2007-05-03
factotum218 - thanks!  If you do happen across anything I wouldn't mind a point in the direction.  Meanwhile, mabye I'll look for some Photoshop tutorials on seamless images.

complexnumber - thanks to you too!  The "make seamless" effect is very close to what I'm trying to do.  I want to be able to do it by hand though, for a little more control over what's repeated and blurred where, etc.  

For example, if I've got a bunch of grapes, rather then having them blend into one another, I want to clone-brush the bottom of a single grape at the top of the picture, and the top of a single grape at the bottom of the picture.  So when the tiles are tiled, instead of grapes blending into grapes, I've still got single grapes.

Regardless, I'd never used the Filters>Map>Tile before.  VERY handy!  That saves me several steps as I can preview what I've just made within Gimp itself, instead of the hassle of loading the picture into a browser.  
:: cheers ::  
So again, thanks!!

-zami

---

### Post by gilrim on 2008-02-03
sudo aptitude install gimp-resynthesizer gimp-texturize

those are nice and quite a bit more sophisticated than the make seamless thingie ;)

---

### Post by zami on 2008-06-03
> **gilrim said:**
> sudo aptitude install gimp-resynthesizer gimp-texturize

those are nice and quite a bit more sophisticated than the make seamless thingie ;)

THAT looks fantastic!  I installed it via the sudo apt above, and it all seemed to go well, and I've restarted GIMP, but I see no new changes.  

Can someone point out what I'm missing?  Is there a new menu entry somewhere I'm overlooking?  

I've never installed a GIMP plug-in before so I could be missing something very basic, and no help will be too remedial!

-zami

---

### Post by dmn_clown on 2008-06-04
ctrl+shift+o > alt+2 > alt+o

brings the edges into the center, use the clone brush, healing brush. or the blur tool depending on what gives the best results.

Repeat the keystrokes to return the center to the edges.

Seamless plugins give horrible results 90% of the time.

---

### Post by digitalis_vulgaris on 2008-06-05
you can make it by hand. Cut image on half, end replace places of parts, so you'll have a perfect matching on edges of image. Than fix middle of image by hand.

---

### Post by zami on 2008-06-30
> **dmn_clown said:**
> ctrl+shift+o > alt+2 > alt+o

brings the edges into the center, use the clone brush, healing brush. or the blur tool depending on what gives the best results.

Repeat the keystrokes to return the center to the edges.

Seamless plugins give horrible results 90% of the time.


What a long lived thread.

This is probably the closest to what I was originally seeking.  Thanks!

Now I just have to master the clone tool.  It doesn't act like I expect it to but that's probably just a matter of learning from one program (Micrografx) to the next (GIMP).  But is there a way to do a mirror-clone?

At any rate, with this quick offset mode I can see what I'm doing, and that's the important part.  Even if there is no mirror-clone option I can probably do what I need with lots of selections and layers and tweaking.  Works  great.  :)

-zami

---

### Post by zami on 2008-06-30
> **digitalis_vulgaris said:**
> you can make it by hand. Cut image on half, end replace places of parts, so you'll have a perfect matching on edges of image. Than fix middle of image by hand.
Another good idea, thanks!

-Laura

---

### Post by grimdeath on 2008-07-02
not sure if you have found your solution yet but if you have photoshop by chance this is one of the coolest plugins I have ever used:

Imagesynth
[http://www.luxology.com/whatismodo/imageSynth.aspx](http://www.luxology.com/whatismodo/imageSynth.aspx)

watch some of the videos on it, freaking amazing stuff. I used it to create seamless tiling textures for a 3D indie game at one time. works like a charm. it's not free though which is the ONLY bummer.

---

