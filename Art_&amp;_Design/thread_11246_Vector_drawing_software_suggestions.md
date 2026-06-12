---
title: "Vector drawing software suggestions?"
date: 2005-01-15
forum: Art &amp; Design
---

### Post by DirtDawg on 2005-01-15
Hey all.
    I've been trying to find a decent vector drawing program for Linux. OppenOffice Draw seems okay, but a little strange (the bezeir curve function works oddly). I think it's pretty much for pie charts and the like. I've also tried Inkscape, which is promising, but I find the lack of a layers pallette disturbing (unless there is one I just can't find). I also can't figure out how to change layer opacity. 
   There's alot of great art from the Linux community so I wondered if anyone has any suggestions? What's your favorite? 
  Many thanks.
   :mrgreen:

---

### Post by Perfect Storm on 2005-01-15
Have you tried Gimp? It's one of the best.

---

### Post by wulf on 2005-01-15
I've been using Inkscape a bit over the past few weeks and I've been really impressed with that.

One thing it doesn't seem to have is the concept of layers, at least not in the same way as packages like the Gimp or, as I recall it, Adobe Illustrator. Each item or group floats on it's own "layer" - you can adjust the transparency of each one via the alpha channel but, once grouped together, you can't adjust overall transparency independently of colour.

However, I think it could certainly be called a "decent" vector graphics package.

What kind of drawings are you wanting to do, and what tools are you used to on other OS's?

Wulf

---

### Post by Yukonjack on 2005-01-15
SODIPODI is pretty good once you get use to it. I used it before and I like it.
sudo apt-get install sodipodi

Vector based drawing program
Sodipodi loads and saves a subset of SVG (Scalable Vector Graphics)
format, a standard maintained by the WWW consortium.

Sodipodi user interface should be familiar from CorelDraw and similar
drawing programs. There are rectangles, ellipses, text items, bitmap
images and freehand curves.
As an added bonus both vector and bitmap objects can have alpha
transparency and can be arbitrarily transformed.

Sodipodi supports multiple opened files and multiple views per file.
Graphics can be printed and exported to png bitmaps.

---

### Post by DirtDawg on 2005-01-15
*Have you tried Gimp? It's one of the best.*
Not for vector art I haven't. I assumed the vector tools were for selection purposes mainly. Perhaps I'm wrong? By the way, GIMP is amazing. I'm completely astounded with it's quality.

*I've been using Inkscape a bit over the past few weeks and I've been really impressed with that... However, I think it could certainly be called a "decent" vector graphics package.*
Yeah I've been impressed with it too. I didn't think about my original post implying Inkscape wasn't decent. It's (plenty) more than decent. I'll choose my words more carefully next time.   
:oops: 

*One thing it doesn't seem to have is the concept of layers, at least not in the same way as packages like the Gimp or, as I recall it, Adobe Illustrator. Each item or group floats on it's own "layer". What kind of drawings are you wanting to do, and what tools are you used to on other OS's? *
Here's the part I can't get used to. I usually draw several objects on several layers, then sort them out in the end so, for example, a hand doesn't end up under an arm or an eye under a head or whatever. I'm used to doing this in pallette form as opposed to highlighting each individual layer in the workspace, then rearranging the orders piece by piece. 
I learned to use vectors in Illustrator. Interestngly (or maybe not :) ), the very reason I have Ubuntu Linux now was because I wanted to check out Inkscape, but Mandrake 9.1 just wouldn't run it. Best decision I ever made. Anyway, I've found, in general,  open source software is designed with the end user in mind more than most commercial products (my guess is because it's designed by end users. I love it!). So in short, I have a windows machine and Illustrator, but I like working on Linux much, much better. If I could switch my entire work space to Linux, I would. 

*SODIPODI is pretty good once you get use to it.*
Cool. I'll check this one out. 

Thanks!

---

### Post by wulf on 2005-01-15
I don't think Inkscape comes quite as close to Illustrator as The Gimp does to Photoshop... yet! If you've got Illustrator, it might be worth checking out Crossover Office (I think that's the right name); I believe that boasted full support for some Adobe products as well as MS Office.

One thing I like about Inkscape is how you can also interact with the underlying XML of the SVG file. It's possible that you could get layer like control by looking at those aspects (Item Properties, XML view) and getting into the habit of giving the object sensible names and group names. I can also see how the Inkscape developers might be able to make use of that to create a layers effect. Of course, I've been working on relatively simple things so far, like some icons and logos, so I rarely need more than about ten or so objects in a design - it might be more complex if you have fifty or a hundred shapes floating about!

I'm certainly looking foward to seeing how it develops in future.

Wulf

---

### Post by Perfect Storm on 2005-01-15
Yep, it's called crossover office. The latest version is 4.1 if you're willing to spend $39.95 for standard and $74.95 for Pro. 
But again at a idealist point of view it would be great to support those programs there's for linux instead.
But it's up to you.

---

### Post by Quest-Master on 2005-01-15
Guys, get the backported .40 Inkscape from the Ubuntu Backports project.

It's totally amazing and has.. layers! :D

---

### Post by xsos on 2005-01-17
i use inkscape, it is awesome tool :D i like, you must try it :D

---

### Post by detonish on 2007-06-14
> **xsos said:**
> i use inkscape, it is awesome tool :D i like, you must try it :D

I've installed it. The first thing I needed to do was to open an Illustrator file (.ai), but I got the following error: 

Couldn't load Perl module Image::Magick.  Images will be skipped.
Can't locate Image/Magick.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 1.
BEGIN failed--compilation aborted at (eval 1) line 1.

Any ideas? 

Cheers, 

David

---

### Post by mech7 on 2007-06-14
Illustrator is the best

---

### Post by tr333 on 2007-06-16
> **detonish said:**
> I've installed it. The first thing I needed to do was to open an Illustrator file (.ai), but I got the following error: 

Couldn't load Perl module Image::Magick.  Images will be skipped.
Can't locate Image/Magick.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 1.
BEGIN failed--compilation aborted at (eval 1) line 1.

Any ideas? 

Cheers, 

David

try installing the following modules:

libgraphics-magick-perl
perlmagick

hopefully this will install the required perl modules for you.

---

### Post by mal on 2007-06-16
You could also try dia (sudo apt-get install dia).

It's a gnome vector drawing tool that has layers.

Mal

---

### Post by mirceade on 2007-06-16
Have you tried **Xara Extreme**? I think it's fabulous.

---

### Post by Hairy_Palms on 2007-06-17
xara LX looks really good, but ill be honest  vector graphics programs scare me :) i like my good ol bitmapped pictures, i just make them big :) :)

EDIT just reading Xara extremem website, didnt realise it can be used to create animated flash movies!!

---

### Post by roomvista on 2007-06-17
hi guys

i am gonna have to go with Inkscape ..the best software  I have used till now.. really cool results.. yuo only have to spend more time but result is outstanding...

nattie

---

### Post by kayosiii on 2007-06-17
Yeah the layers palette is the last item in the layers menu... (in version 0.41 anyways)...
Hope that helps

---

### Post by BRAXS69 on 2007-06-17
i suggest **inkscape** or **xara linux extreme** both have layer support and both are excellent vector apps.

i kind of taken a liking to inkscape after i to figured out how to show the layer panel...(layer> layer_s_... Shift+Ctrl+L) lol 
and because it dose support a lot more then xara, however xara is very fast and seems to have a few tools that i like a little more then inkscape... 

```
to install inkscape
sudo apt-get install inkscape

to install xara extreme 
sudo apt-get install xaralx xaralx-svg imagemagick
```

a few previews for that matter.....

---

### Post by detonish on 2007-06-17
> **tr333 said:**
> try installing the following modules:

libgraphics-magick-perl
perlmagick

hopefully this will install the required perl modules for you.

Hey mate, 

I did what you suggested but got a different error message. 

Use of uninitialized value in subtraction (-) at /usr/share/inkscape/extensions/ill2svg.pl line 318, <> chunk 128.
Argument "^W^X" isn't numeric in printf at /usr/share/inkscape/extensions/ill2svg.pl line 323, <> chunk 128.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 324, <> chunk 128.
Use of uninitialized value in printf at /usr/share/inkscape/extensions/ill2svg.pl line 325, <> chunk 128.
Use of uninitialized value in concatenation (.) or string at /usr/share/inkscape/extensions/ill2svg.pl line 329, <> chunk 128.


Any idea? 

Thanks

---

### Post by bakermiller on 2007-06-17
you get that error when you import .ai to inkscape?
i've never been able to do it. 

what i do is I export .svg from illustrator and import .svg to inkscape. 

You lose all layers swatches, brushes, colors are off, but you keep your paths :p

...unless you can tell me how to use this...

[http://www.xs4all.nl/~hanwen/public/software/ai2svg.py](http://www.xs4all.nl/~hanwen/public/software/ai2svg.py)

... maybe someone who knows python can help out with this...

---

### Post by JanvL on 2007-06-18
Hi

I use Inkscape 0.45
and Xara LX.

Installed them with the autopackage for so you have the latest Inkscape.
Do not forget to uninstall the original inkscape first!

Xara has the best GUI.
But Inkscape has some very nice aspects too.

Just use them both depending on the job.


Jan

---

### Post by Golyadkin on 2007-06-19
I was also looking for a good vector graphics editor, and started using Inkscape when people still used Sodipodi. Now on Ubuntu, Inkscape kicks ***. There are also quite a lot of video tutorials on video.google.com about Inkscape.

---

### Post by switchcode on 2007-08-28
I also am STILL searching for anything that can fill the hole that freehandMX has left. For flash development, there is nothing on linux that comes anywhere close. For instance; You can copy from freehandMX directly into flash. Right now, if I cant be bothered rebooting into windows, Im stuck with drawing in either sodipodi (nice but severely limited- No grid snap?? wdf?) or Inkscape, saving to SVG, loading into Scribus, exporting to .EPS, then importing .EPS into flash (which runs nicely on wine).
  Im pretty desparate to get freehandMX running on wine. Any ideas?

---

### Post by multifaceted on 2007-08-30
Inkscape is a really great package.  It's extremely intuitive right off of the start however, it does lack the layering advantages of Adobe's graphics products... which is can be a problem for those who often expand on thought. Overall, it creates vectors quickly and painlessly.

---

### Post by oldefoxx on 2009-11-08
I've never seen a drawing package that would do exactly what I had in mind, which is this:

Give actual x,y,z measurements, so that the object would appear already set to scale.  Initially the z dimension would be hidden.

Be able to rotate the object and slant our view of it.  For instance, in mechanical drawings, you generally seek a slightly higher view and see the whole object from one side.  The slants are typically 30 degrees off the horizontal.  Applied perspective can be allowed once the objects are in their final resting places.

In moving the object among other objects, be able to control the layers so that it can move in front of or behind other objects,   Keep those other objects locked in place so that they do not **** about as this one is moved.  Once in place. the new object can be added to the others and create or extend a group.  The whole group can be locked into place, or move about, even rotated so as to make it fit properly among other objects.  Objects can be color designated, subject to a light source and shadows, and either opaque or transparent so that some or all of the objects behind can show through.

What I am faced with instead is the need to draw rectangles just to ensure that lines are exactly vertical or horizontal, and having to drag the sides in and out to try and achive an exact emulation as to scale and size.  These are just rectangles, and achieving angled views such as being slightly above or slightly to one side means trying to change the rectangle itself. or append and hide the areas where some triangles have to be made and placed to give the appearance of an angled view or placement.  That third dimension, known as z, would interchange with either the x or y in some placements or views, and a critical factor is the degree in which any angle rotation effects the viewed depth of field.  When a surface with z=0 faces us, we only perceive the x and y effects.  Turned to its side, we would see instead where x=0 and the viewed dimensions are composed of only y and z.  The same would hold if seen from directly above or below, or the object is rotated 90 degrees, and now the measurements are onluy seen as being x and z.  Then there are all the intermediate angles where some depth of vision now means we see the sides, heighth, or depth as being shortened due to the effects of seeing objects at an angle.

I want to begin a drawing with a sheet of plywood that is precisely 60" by 16" by 5/8ths" in thickness.  You know how hard it is to draw two overlapping 2D sheets that overlap at a visual distance of 5/8ths inches, and have that hold even if doctored a bit to add some apparent view angling or a tilt of sheet itself?  You might struggle with it and get something that looks about right, but what of the next sheet that has to be then drawn?  If any of the measurements are different, you could try dragging the sides in or out to achieve new effects, but if you have an effective 3D construct as seen in 2 dimensions, then some visual distortions to one or more of the dimensions or relatonships between the x, y, and z settings.

See, the idea here is to take the overall dimensions sought, then work out how the individual components can be sized and joined to fit with the overall dimensions, and even exactly how they have to be cut and how much material is involved, even before turning on the cutting machines or doing any buys.  Get it right, and you can determine beforehand the exact quantity of plywod and what-nots, and priced the whole job accordingly.  Doing it right also means no belated surprises about what the job entails.

---

### Post by mal on 2009-11-08
> **oldefoxx said:**
> I've never seen a drawing package that would do exactly what I had in mind, which is this:

Give actual x,y,z measurements, so that the object would appear already set to scale.  Initially the z dimension would be hidden.

Be able to rotate the object and slant our view of it.  For instance, in mechanical drawings, you generally seek a slightly higher view and see the whole object from one side.  The slants are typically 30 degrees off the horizontal.  Applied perspective can be allowed once the objects are in their final resting places.

In moving the object among other objects, be able to control the layers so that it can move in front of or behind other objects,   Keep those other objects locked in place so that they do not **** about as this one is moved.  Once in place. the new object can be added to the others and create or extend a group.  The whole group can be locked into place, or move about, even rotated so as to make it fit properly among other objects.  Objects can be color designated, subject to a light source and shadows, and either opaque or transparent so that some or all of the objects behind can show through.

What I am faced with instead is the need to draw rectangles just to ensure that lines are exactly vertical or horizontal, and having to drag the sides in and out to try and achive an exact emulation as to scale and size.  These are just rectangles, and achieving angled views such as being slightly above or slightly to one side means trying to change the rectangle itself. or append and hide the areas where some triangles have to be made and placed to give the appearance of an angled view or placement.  That third dimension, known as z, would interchange with either the x or y in some placements or views, and a critical factor is the degree in which any angle rotation effects the viewed depth of field.  When a surface with z=0 faces us, we only perceive the x and y effects.  Turned to its side, we would see instead where x=0 and the viewed dimensions are composed of only y and z.  The same would hold if seen from directly above or below, or the object is rotated 90 degrees, and now the measurements are onluy seen as being x and z.  Then there are all the intermediate angles where some depth of vision now means we see the sides, heighth, or depth as being shortened due to the effects of seeing objects at an angle.

I want to begin a drawing with a sheet of plywood that is precisely 60" by 16" by 5/8ths" in thickness.  You know how hard it is to draw two overlapping 2D sheets that overlap at a visual distance of 5/8ths inches, and have that hold even if doctored a bit to add some apparent view angling or a tilt of sheet itself?  You might struggle with it and get something that looks about right, but what of the next sheet that has to be then drawn?  If any of the measurements are different, you could try dragging the sides in or out to achieve new effects, but if you have an effective 3D construct as seen in 2 dimensions, then some visual distortions to one or more of the dimensions or relatonships between the x, y, and z settings.

See, the idea here is to take the overall dimensions sought, then work out how the individual components can be sized and joined to fit with the overall dimensions, and even exactly how they have to be cut and how much material is involved, even before turning on the cutting machines or doing any buys.  Get it right, and you can determine beforehand the exact quantity of plywod and what-nots, and priced the whole job accordingly.  Doing it right also means no belated surprises about what the job entails.

It sounds like what you need is a decent CAD package with 3D capability.  As far as I know, the only suitable options are high priced commercial applications, like AutoCAD.

QCAD is a reasonable CAD package that is available in the Ubuntu repositories, but it is strictly 2D only and will not easily cope with rotating views or isometric projections.

Mal

---

