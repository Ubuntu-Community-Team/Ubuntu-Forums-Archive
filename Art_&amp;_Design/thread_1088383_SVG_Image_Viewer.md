---
title: "SVG Image Viewer?"
date: 2009-03-06
forum: Art &amp; Design
---

### Post by bj0 on 2009-03-06
Is there a good (simple/fast) program that can view SVG files correctly?  I know most image viewing programs can open them, but the ones I've tried so far (Gnome's Image Viewer, GQview, F-Spot) all seem to render them to bitmaps (rasterize?) when they are opened, and then they don't zoom correctly (they get real blurry).

---

### Post by kayosiii on 2009-03-06
Inkview I think it is part of the inkscape package may fit your needs.

---

### Post by skillllllz on 2009-03-06
You can also try Xara Xtreme [http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

---

### Post by bj0 on 2009-03-06
Wow, nice quick answers.  Both are better than what i found googling for over an hour.

Inkview - I had Inkscape, but I didn't know about this little program.  It seems pretty nice except that it can't really do anything except display the image as it is.  As far as I can tell there is no zoom ability (aside from the full-screen view).


Xara - Seems nice, but it seems to have trouble with text.  Also it's a full blown editor, I was wondering if there is something more lightweight, like just a viewer.

Thanks for the ideas though, keep them coming :)

---

### Post by smartboyathome on 2009-03-06
> **skillllllz said:**
> You can also try Xara Xtreme [http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

Xara doesn't do SVGs well. I would not recommend it if you need SVGs.

There will be no "real" svg viewer that will do all you need. What you need to do is save your svg as a "plain svg" within Inkscape, then it can be viewed correctly by the many image viewers. The problem is that Inkscape has some inkscape-only features which won't be rendered correctly unless you have a inkscape-compatible viewer (ie, inkview). By saving it as a plain SVG (not an inkscape SVG) you are getting rid of those inkscape-only features, and thus are able to view it in other viewers correctly.

---

### Post by Bölvaður on 2009-03-06
firefox?

---

### Post by smartboyathome on 2009-03-06
> **Bölvaður said:**
> firefox?

It has some problems rendering stuff like text. Only way to fix it is to convert the text to paths, which makes the text no longer able to be edited.

---

### Post by bj0 on 2009-03-07
> **smartboyathome said:**
> Xara doesn't do SVGs well. I would not recommend it if you need SVGs.

There will be no "real" svg viewer that will do all you need. What you need to do is save your svg as a "plain svg" within Inkscape, then it can be viewed correctly by the many image viewers. The problem is that Inkscape has some inkscape-only features which won't be rendered correctly unless you have a inkscape-compatible viewer (ie, inkview). By saving it as a plain SVG (not an inkscape SVG) you are getting rid of those inkscape-only features, and thus are able to view it in other viewers correctly.


It's not that the image viewers are displaying the svg files incorrectly, it is that they are scaling (zooming) them incorrectly.  It's the same with any svg, not inkscape, and it's my guess that all the image viewers I've tried work the same:  they open the svg file and render it to a raster image.  All the zooming is done on this raster image.

The problem is that zooming a raster image makes it blurry, whereas a vector image (svg) should be able to scale to arbitrary sizes without being blurry.  So the problem is likely one of implementation for the programs I've tried.  It took me a while to find some examples of it being done the 'correct' way in Python, but I found this:
[http://cairographics.org/cookbook/](http://cairographics.org/cookbook/)

And I wrote a little python script that demonstrates what I'm talking about.

You just run it as: svg_compare.py <filename> 
and it opens up an svg and displays it using an svg library and using gtk's raster library.  You can zoom with the mouse wheel or -/+ keys and drag the image around.  You can also press 'I' to cycle through the interpolation methods for raster zoooming.  If you zoom in enough you can see there is quite a difference.

---

### Post by nikodll on 2010-09-03
in case someone still needs a similar program - xsvg (from [http://cairographics.org](http://cairographics.org)) can do the job

---

### Post by nikodll on 2010-09-03
--

---

### Post by sdaau on 2010-12-24
Hi all, 

Can someone explain me why this thread is closed?

[SVG Image Viewer? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1088383")

I just wanted to post my script [svg_refreshview.py]("http://sdaaubckp.svn.sourceforge.net/viewvc/sdaaubckp/single-scripts/svg_refreshview.py?view=markup") there, derived on one of the scripts I found there... but I can't: "thread's closed" :) 

I mean, if it was something like testing for a historic legacy version, I'd understand - but a question on "SVG image viewer" should pretty much stay open, I guess?? 

Nevermind.. if anyone knows what is the logic, I'd like to know :)

Cheers!

---

### Post by JOHNNYG713 on 2010-12-24
IMHO! Some of the Admins and Mod's around here have a Hitler complex!:P I will check out your script and get back !:p

---

### Post by overdrank on 2010-12-24
> **sdaau said:**
> Hi all, 

Can someone explain me why this thread is closed?

[SVG Image Viewer? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1088383")

I just wanted to post my script [svg_refreshview.py]("http://sdaaubckp.svn.sourceforge.net/viewvc/sdaaubckp/single-scripts/svg_refreshview.py?view=markup") there, derived on one of the scripts I found there... but I can't: "thread's closed" :) 

I mean, if it was something like testing for a historic legacy version, I'd understand - but a question on "SVG image viewer" should pretty much stay open, I guess?? 

Nevermind.. if anyone knows what is the logic, I'd like to know :)

Cheers!

Thread reopened and merged. :)

> **JOHNNYG713 said:**
> IMHO! Some of the Admins and Mod's around here have a Hitler complex!:P I will check out your script and get back !:p
):P

---

### Post by ShadowDragon on 2011-03-26
I was also looking for a decent zooming svg-viewer. I needed it to view package dependency graphs. And I found rsvg-view in the librsvg2-bin package which does the job remarkably well.

Example usage:
```
apt-rdepends --dotty xorg | dot -Tsvg | rsvg-view --stdin
```

---

### Post by jorok_tupur on 2011-03-26
> **bj0 said:**
> Is there a good (simple/fast) program that can view SVG files correctly?  I know most image viewing programs can open them, but the ones I've tried so far (Gnome's Image Viewer, GQview, F-Spot) all seem to render them to bitmaps (rasterize?) when they are opened, and then they don't zoom correctly (they get real blurry).

I recommend [Squiggle from the Batik Toolkit]("http://xmlgraphics.apache.org/batik/tools/browser.html"). It zooms correctly (not blurry).

---

### Post by Tommy06 on 2011-03-29
Does the problem persist&#65311;
In the case i think you’d better off not using SVG image viewer at all and just using a good image viewer to manage your photos&#65292;
Google ”jquery based image viewer“there are dozens of them&#12290;

---

### Post by Tommy06 on 2011-03-30
There  are millions of them, you can google the image viewe which can support the format you want .
If you have not much time.Try this  link:   [http://www.brightyoursite.com/blog/2010/02/21/jquery-based-image-viewer/](http://www.brightyoursite.com/blog/2010/02/21/jquery-based-image-viewer/)   [URL="http://www.brightyoursite.com/blog/2010/02/21/jquery-based-image-viewer/"]
[/URL]

---

