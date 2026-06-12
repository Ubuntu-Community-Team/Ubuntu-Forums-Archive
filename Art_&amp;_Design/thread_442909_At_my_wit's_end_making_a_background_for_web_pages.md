---
title: "At my wit's end making a background for web pages"
date: 2007-05-14
forum: Art &amp; Design
---

### Post by Peter Mount on 2007-05-14
Hello

I just want to make a background and I'm having trouble with the different graphics packages. I've tried The Gimp, Krita and Inkscape.

I'm trying to make a horizontal white rectangle with a small grey rectangle at one end and have 1 px wide solid lines (to server as borders) on the left and right edges of the rectangles.

Inkscape is very slow on my Pentium 2-350 with the Kubuntu Feisty Desktop. I could try downloading the Xubuntu-Desktop to see if that helps.

I don't know how to make straignt lines in The Gimp. In Krita once I make a rectangle I don't know how to move it or resize it or change it's colour or change it's borders or anything.

Can somebody please point me to either:

1  Simple to use Linux graphics program that any idiot can use or
2  Helpful tutorials for Linux graphics newbies like me?

Thanks

---

### Post by dfreer on 2007-05-14
here's a few gimp links (mostly have to deal with so called Web 2.0 effects, not much help):
[http://binnyva.blogspot.com/2006/12/creating-shadows-in-gimp.html](http://binnyva.blogspot.com/2006/12/creating-shadows-in-gimp.html)
[http://www.gimp.org/tutorials/Creating_Icons/](http://www.gimp.org/tutorials/Creating_Icons/)
[http://www.tutorialized.com/tutorial/Make-a-button-with-rounded-corners/20823](http://www.tutorialized.com/tutorial/Make-a-button-with-rounded-corners/20823)
[http://www.technomono.com/tutorials/gimp/mac-button/index.php](http://www.technomono.com/tutorials/gimp/mac-button/index.php)
[http://binnyva.blogspot.com/2006/12/using-gimp-to-make-web-20-buttons-and.html](http://binnyva.blogspot.com/2006/12/using-gimp-to-make-web-20-buttons-and.html)

when I draw straight lines, I click at one spot, and then hold down shift (or left ctrl can't remember), and while holding down a line will appear. simply click to place)

gimp is the main graphics program but it is quite daunting to new users. inkscape is good for SVG icon making.

EDIT: on second thought, if that is all you are trying to accomplish you could use CSS to make your image.

also, there is a rectangle drawing button in gimp that lets you draw perfect straight lines. you can then move, spin and reposition the box you made.

---

### Post by Peter Mount on 2007-05-14
Thanks dfreer

I'll look at those links. I'll look at CSS as well plus that rectangle drawing button.

Have a good day

---

### Post by lyceum on 2007-05-14
[http://www.amazon.com/Beginning-GIMP-Novice-Professional/dp/1590595874/ref=pd_bbs_sr_1/103-7182138-3908614?ie=UTF8&s=books&qid=1179150392&sr=8-1](http://www.amazon.com/Beginning-GIMP-Novice-Professional/dp/1590595874/ref=pd_bbs_sr_1/103-7182138-3908614?ie=UTF8&s=books&qid=1179150392&sr=8-1)

get this book, it was the best $33 I spent.

---

### Post by maruchan on 2007-05-14
> I'm trying to make a horizontal white rectangle with a small grey rectangle at one end and have 1 px wide solid lines (to server as borders) on the left and right edges of the rectangles.

Visually it's hard to imagine what you're wanting here, but I made a short demo of some simple techniques that might help you in GIMP:

[http://www.friendlyskies.net/gimpquickdemo.ogg](http://www.friendlyskies.net/gimpquickdemo.ogg) (6.5MB OGG, no audio, use VLC to play)

1. Select all, then "shrink" the selection by one pixel. Invert the selection (this selects the 1px along the edge), and use the fill bucket to give yourself a 1px border.
2. Use the "subtract from selection" mode of the selection tool to modify the shape of a selected area.
3. Sometimes the "show layer boundary" option can confuse new GIMPers when they're working with selections, because the layer boundary resembles a selection. So I show you how to turn it off. (For advanced use it's helpful to show layer boundaries)

To draw straight lines in the GIMP, select a tool, e.g. brush, pencil, etc., and hold SHIFT while drawing with it.

Also, a Pentium 2 is going to run stuff slowly in general. :)

---

