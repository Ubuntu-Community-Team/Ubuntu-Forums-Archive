---
title: "GIMP - convert png to svg ?"
date: 2008-10-24
forum: Art &amp; Design
---

### Post by Sceiron on 2008-10-24
I have read that this is possible to do in gimp, but i cant find out how.
Tried to "Save as" but there is no extension for .svg...
Using GIMP 2.4.5
Am i missing som add-ons?

---

### Post by blackened on 2008-10-24
Unless there's an auto-trace function built in, then converting from raster to vector is usually a manual job. I think inkscape has a built-in auto-trace function, but, from what I've read, it does a mediocre job at best.

Your best bet, as far as quality goes, would be to use Inkscape, import a (preferably large, 256x256 px) png and then convert it to vector by hand.

---

### Post by sloggerkhan on 2008-10-24
You can use inkcape, if you get the settings right it will do a decent job, particularly for logo-style images. There are a lot of settings to tweak and it's not at all obvious what they do, though.

---

### Post by innovati on 2008-10-24
from what I understand, the way to export an SVG from the GIMP was to export Paths.  If you were to open a PNG in the GIMP there would be no paths yet, but any paths you make from the PNG should be able to be exported.

SVG is a vector graphics format, PNG is a bitmapped image format - they di very different things.  SVG can contain embedded bitmapped graphics, but that wouldn't be desirable, nor would it save you space.

If you desire a vector trace of the PNG, the Auto-trace in Inkscape (shift+alt+B) is the best tracer I've ever used, and I believe it's based on PoTrace.  In the GIMP you should be able to select colour regions with the colour select tool, and then create Paths from selection.

Hope this helps...

---

### Post by dariusdwtt on 2008-12-07
bump

---

### Post by smartboyathome on 2008-12-07
Like others said, theres Inkscape, but your best bet is tracing the raster graphic by hand, since there isn't a tool yet which can do gradients and such correctly (they just use a bunch of different colored objects next to each other).

---

### Post by lingenfr on 2009-04-12
Then what happened to the gimp-svg package that was in previous releases? All I want to do is create a stinking menu icon, not a video game. This is a bit ridiculous.

---

### Post by Dadster on 2009-04-12
Try here [http://www.rw-designer.com/online_icon_maker.php](http://www.rw-designer.com/online_icon_maker.php)  hopefully that helps you

---

### Post by 73ckn797 on 2009-04-12
Remembering something from windows, I made a copy of a jpg file and renamed the extension to svg. I then, as a test, created a launcher on the desktop. Once that was done I right clicked the launcher, selected properties and clicked on the icon and selected the copied and renamed extension file. It loaded as the icon for the launcher. Really quite simple!

---

### Post by smartboyathome on 2009-04-13
> **73ckn797 said:**
> Remembering something from windows, I made a copy of a jpg file and renamed the extension to svg. I then, as a test, created a launcher on the desktop. Once that was done I right clicked the launcher, selected properties and clicked on the icon and selected the copied and renamed extension file. It loaded as the icon for the launcher. Really quite simple!

That doesn't create a "true" svg, though. To create a true SVG, one must trace manually.

And the GIMP SVG package was just for importing SVGs. Now that the feature is built in, there is no need for that. I would recommend creating your logo in Inkscape if you really want it as SVG.

---

### Post by kayosiii on 2009-04-13
SVG are not bitmap files but SVG files can contain embedded bitmaps but doing things that way kind of defeats the purpose of using SVG in the first place... If you still want to use the embedded method, try the following, Open up an existing svg Icon file in Inkscape, Have a look at the sizing layers etc. save a copy with the new icon name. You can drag and drop a PNG image from a file manager into Inkscape then scale it to fit the dimensions of the Icon then delete the original material. Save this new svg file.

---

### Post by 73ckn797 on 2009-04-13
> **smartboyathome said:**
> That doesn't create a "true" svg, though. To create a true SVG, one must trace manually.

And the GIMP SVG package was just for importing SVGs. Now that the feature is built in, there is no need for that. I would recommend creating your logo in Inkscape if you really want it as SVG.

I realize it is not a true svg based on the resulting file size not changing. I actually had not tried it to see what it would do. It worked in essence though not the same as how it worked in Windows. I will look into the SVG package for future uses of creating icon files.

---

### Post by eb sol on 2009-11-27
[SIZE="4"]Check out [this link]("http://ubuntuforums.org/showthread.php?t=567590") .. It might help ;)[/SIZE]

---

### Post by stoneage on 2010-01-23
Have you considered SVGpage:-
[http://www.getdeb.net/software/SVGpage](http://www.getdeb.net/software/SVGpage)

---

### Post by blackened on 2010-01-23
Hmm, hadn't heard of SVGpage, I'll give it a try.

---

### Post by WadeH2o on 2010-02-16
> **stoneage said:**
> Have you considered SVGpage:-
[http://www.getdeb.net/software/SVGpage](http://www.getdeb.net/software/SVGpage)

When I click the install link it seems to download but can't find SVGpage ...?? 

Same results with Terminal:
```
sudo apt-get install svgpage
```

---

### Post by 23dornot23d on 2010-02-17
Open your png file in gimp save it as a jpg

then open it in inkskape ..... do a path trace

and then update create .... in the trace mode

select it the new object

then save as a SVG ..... or whatever ....  took the zebra off this mural

[http://photocamel.com/forum/speed-challenges/99897-speed-challenge-218-a.html](http://photocamel.com/forum/speed-challenges/99897-speed-challenge-218-a.html)

DXF is good .... as it allows imports into Blender .....

[http://i46.tinypic.com/6eolco.jpg](http://i46.tinypic.com/6eolco.jpg)


This was just a test .... but if you have good outlines you should get a pretty good result .... I tried it on a couple of images ....

But it works the same for SVG files ...... hope this helps ..... 

Here was a test with the UBUNTU logos .... differrent colours and shades ..... so it might be best in black .... rather than colour ... 

[IMG]http://i50.tinypic.com/29esnpf.jpg[/IMG]

Totally scaleable ... 

[IMG]http://i46.tinypic.com/r6y0e8.jpg[/IMG]

Some of the curves are better than others ,,,, I just did a quick extrude on this one ... and it looks pretty smooth to me .....

but what a quick way to get and move vectors into a 3D world ..... from any photo or diagram ......

I can make use of it now ..... thanks for posting .... and all the good replies too ........

---

### Post by stoneage on 2010-02-17
> **WadeH2o said:**
> When I click the install link it seems to download but can't find SVGpage ...?? 

Same results with Terminal:
```
sudo apt-get install svgpage
```
Did you do this:-

[ATTACH]147349[/ATTACH]

---

