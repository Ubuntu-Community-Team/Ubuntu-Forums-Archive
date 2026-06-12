---
title: "Comic Book Speech Bubble creator?"
date: 2011-06-14
forum: Art &amp; Design
---

### Post by Sofox on 2011-06-14
Hey,
I make comics every so often and I think I've noticed a gap in the graphics software market (at least from what I know). Namely for speech bubbles.
Now while you can roll your own speech bubbles in anything from Gimp to Photoshop, they take time, are fiddly, usually require you to do the text and bubbles independentally and can be a pain to continually adjust as you try to tweak it the way you want. 

What I have in mind is a fast "5 second" solution for this, either as a plugin or standalone application:

1- The person clicks where on the comic they want the text.
2- They type out the text of the character, a word balloon immediately forms around it.
3- By clicking and dragging, the user can resize the word balloon and aim the "tail" of the speech bubble to whoever's talking
4- They will most likely have already set up the style, font and transpanrency of the bubble, so at this stage they can just go onto the next bubble!

I'm sure this has been done before, commercial Manga Studio does this which some comic artists have had to use after assembling their entire comic in another program, but I can't think of any free(-dom) software that does the same.

Any thoughts or existing software out there for this?

---

### Post by ngrieb on 2011-06-14
I think gimp might have a plug-in like this already...not to mention all of the office programs out there. 

Gimp -> Filters -> GFig: draw an elipse and add a triangle, then erase elipse overlap (takes all of 3 seconds). That or save a bubble as an svg image using Inkscape, then stretch and manipulate it without any loss of quality.

---

### Post by alaukikyo on 2011-06-15
try [TBO]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBgQFjAA&url=http%3A%2F%2Flive.gnome.org%2FTBO&rct=j&q=TBO%20gnome&ei=QWb4Tb6EPc_irAe-v9yZCA&usg=AFQjCNEPAVMruQJJte-c1JxqORdqnwANYA&sig2=7a_nhYVwM5yAh-YBWG5D6w&cad=rja") .

---

### Post by Newfoundlander on 2011-06-15
I used to work in the comic publishing industry many years ago and Inkscape is very quick at making custom speech balloons.  Perhaps I should do a tutorial video?

---

### Post by SoFl W on 2011-06-15
> **ngrieb said:**
> I think gimp might have a plug-in like this  already
Gimp -> Filters -> GFig: 

Filters-> Render-> Gfig.
Thank you for pointing it out, not sure if I ever used it before.

> **Newfoundlander said:**
> I used to work in the comic publishing industry many years ago and Inkscape is very quick at making custom speech balloons.  Perhaps I should do a tutorial video?

How about listing the steps as text in a message?  Much easier to follow, and take each step one by one.

---

### Post by ragtag on 2011-07-25
This is an interesting post. I use both Manga Studio and GIMP, and would love to see some of the comic specific features found in Manga Studio, implemented in the GIMP.

What I've done when creating speech bubbles in GIMP is to use the oval selection tool, convert it to a path, and simply add a tail to the path. Finally I fill it with white, and then run Stroke path to get a line around it. It works ok, but takes a few steps. If (or rather when) I do more comics in GIMP, I'll probably write a small plug-in to speed some of that up. I wouldn't mind still drawing the paths, but maybe I could automate the filling and stroking. In Manga Studio, you enter the text, pick a style for your bubble, and draw out a simple path for your tail. It's very quick and easy, and you can always go in later and adjust the shape of the bubble if you want, as it's vector based.

That said, there are a couple of other features in Manga Studio that are interesting. The panel tools there are really excellent and quick to use. You create a panel layer (a sort of path layer), and then just cut it up with the panel tool, to make the gutters between the panels. This too can be easily replicated in GIMP using box selection, paths and stroke path again. Manga Studio also includes panel layers, which are basically sub-images for each panel that open in their own window, with their own set of layers and so on. This could in theory be implemented in the GIMP, but is really not needed.

One of the more interesting features though is the story mode. It basically a thumbnail view of your entire comic book, where you can add, re-order and delete pages, and get a general overview of your story. Double clicking on a page, opens it up for editing. It also includes related features, such as exporting the whole comic book to different formats and scales. If you have a 100 page comic, and want to export it to jpg's for web use, this comes in very handy. :) GAP can do some of this in a round-about way, but it's rather complex and really made for a different purpose. This is probably the comic specific feature I would like to see most in the GIMP, but would be a little harder to implement as I believe you need to make your own GTK interface for it as the ones provided by the plug-in API are a bit to basic.

I may get around to coding some of these some day, if I'm not too busy with work and actually drawing comics. :)

---

### Post by 23dornot23d on 2011-07-25
Quite a nice tutorial here already done - [**LINK**]("http://www.gimptalk.com/index.php?/topic/49450-tutorial-comic-making-using-mypaint-gimp-and-inkscape/")

But it would be good to see another one ..... if its more specific to the users needs ....

---

### Post by chib on 2011-07-28
I usually just make one large one with two separate layers, one of the balloon and the other with the little point so I can just copy it and move the arrow accordingly.  Photoshop btw.

---

### Post by Gemnoc on 2011-07-31
> **alaukikyo said:**
> try [TBO]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBgQFjAA&url=http%3A%2F%2Flive.gnome.org%2FTBO&rct=j&q=TBO%20gnome&ei=QWb4Tb6EPc_irAe-v9yZCA&usg=AFQjCNEPAVMruQJJte-c1JxqORdqnwANYA&sig2=7a_nhYVwM5yAh-YBWG5D6w&cad=rja") .

TBO seems fun! Unfortunately it is not easy to install, at least not on Ubuntu 10.04 LTS. I tried to build it from the Git repository but found out the code was switched to Gtk+3 back in April, so no can do on Lucid. I found a 32-Bit deb package on the author's trac: [http://trac.danigm.net/tbo/wiki/downloads](http://trac.danigm.net/tbo/wiki/downloads)

But I am on 64-Bit! I found on the author's blog (in spanish) that a commenter had made a package available for Lucid on her PPA: [https://launchpad.net/~miry/+archive/ppa/+packages?batch=75&memo=75&start=75](https://launchpad.net/~miry/+archive/ppa/+packages?batch=75&memo=75&start=75)

The package is rather dated (last november), but it at least allowed me to try the software. You don't even have to know how to draw, comics characters are provided, you just need to drag & drop them on the page.

---

