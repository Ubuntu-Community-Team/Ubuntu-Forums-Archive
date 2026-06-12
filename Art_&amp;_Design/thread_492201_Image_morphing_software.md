---
title: "Image morphing software"
date: 2007-07-04
forum: Art &amp; Design
---

### Post by koosfoto.hu on 2007-07-04
Greetings!

I am looking for a progrum running under Ubuntu which can make image morphing videos and animated gif files.
Under windows my choise would be the [FantaMorph ]("http://www.fantamorph.com")

Thanks,

Tamas

---

### Post by hikaricore on 2007-07-04
Here's a good start.

[http://www.tucows.com/Linux/DesignTools/Image/Morph/](http://www.tucows.com/Linux/DesignTools/Image/Morph/)
[http://www.cg.tuwien.ac.at/research/ca/mrm/](http://www.cg.tuwien.ac.at/research/ca/mrm/)

I have no idea if any of these are in the repos as I'm at work right now and slightly busy.  >.<

---

### Post by IYY on 2007-07-05
There's a program called gtkmorph (an update of xmorph). Both are in the repositories. Problem is that the interface is quite counterintuitive.

---

### Post by koosfoto.hu on 2007-07-05
Thanks hikaricore!

Multi-Resolution Image Morphing was last updated on the March 23, 1998.

Tucows about the same... 

It seems, that they are old, and not maintaned anymore... 

Does anyone has a newer idea?

Thanks.


Tamas

---

### Post by koosfoto.hu on 2007-07-05
Thanks IYY!

I have installed it, and trying it out...

Greetings,

Tamas

---

### Post by Hampster on 2009-01-08
Hi. Team.
I just downloaded gtkmorph from Synaptic Package manager along with the support stuff.  Can anyone tell me where it went and how I can find it? 
( and Run It)  Thanks in anticipation.

---

### Post by Gannin on 2009-02-05
The gtkmorph package doesn't install an icon, so you'll have to go to Applications > Accessories > Terminal and type "gtkmorph" without the quotes.

---

### Post by hikaricore on 2009-02-20
I've found that Sqirlz Morph: [http://www.xiberpix.net/files/SqirlzMorph.zip](http://www.xiberpix.net/files/SqirlzMorph.zip)

Does a nice job under WINE. [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4578](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4578)

---

### Post by grishashvili on 2009-03-04
Hi Everyone,

I have a question, is there such a thing as a command line morph tool? Does any of the tools mentioned above support command line usage?

I just need to automate some task that requires hundreds of morphs...

Thanks a lot
Henry

---

### Post by The Judderman on 2009-04-03
Just out of interest, I've found that the software WinMorph seems to work well under WINE (I have it installed, but not tried to do much with it yet):

[http://www.debugmode.com/winmorph/](http://www.debugmode.com/winmorph/)

Cheers,

the Judderman

---

### Post by hellocatfood on 2010-01-12
Does anyone know of any native Linux apps that are still maintained that can do this?

---

### Post by szirakitamas on 2010-10-20
hellocatfood
hi, gtkmorph is still in repos.

---

### Post by hellocatfood on 2010-10-20
I found that program eventually but it looks like ancient and is really difficult to use. Providing this as a solution I think really does a disservice to the overall polish feel of Ubuntu

---

### Post by kilolife on 2011-04-27
mkdir temp
cp *.JPG temp/.
mogrify -resize 800x800  temp/*.JPG
convert temp/*.JPG -delay 10 -morph 10 temp/%05d.jpg
ffmpeg -r 25 -qscale 2  -i temp/%05d.jpg output.mp4

from [http://www.itforeveryone.co.uk/image-to-video.html](http://www.itforeveryone.co.uk/image-to-video.html)

---

### Post by hellocatfood on 2012-01-09
> **kilolife said:**
> mkdir temp
cp *.JPG temp/.
mogrify -resize 800x800  temp/*.JPG
convert temp/*.JPG -delay 10 -morph 10 temp/%05d.jpg
ffmpeg -r 25 -qscale 2  -i temp/%05d.jpg output.mp4

from [http://www.itforeveryone.co.uk/image-to-video.html](http://www.itforeveryone.co.uk/image-to-video.html)

Thanks for the effort but that codedoesn't morph between two images, it just fades between them and offers no control over which parts are morphed. For an example of what I'm looking for look at [Facemorpher](http://www.facemorpher.com/)

---

### Post by cantormath on 2012-01-17
wine+Sqirlz_Morph works...

---

### Post by hellocatfood on 2012-02-06
To quote myself:

> **hellocatfood said:**
> Does anyone know of any **native** Linux apps that are still maintained that can do this?

---

### Post by snowguy on 2012-02-07
> **hellocatfood said:**
> I found that program eventually but it looks like ancient and is really difficult to use. Providing this as a solution I think really does a disservice to the overall polish feel of Ubuntu

I've used it and agree 100% it is a real pain. When I finally figured it out I wrote some instructions to myself just in case I ever wanted to do it again--likely not. 

There is a gimp plugin that does morphs and uses essentially the same backend. From what I've seen in tutorials (i haven't tried myself) it is easier to use. The google search will come back with plenty of help:

[http://www.google.com/search?&q=gimp+image+morph](http://www.google.com/search?&q=gimp+image+morph)

---

### Post by the dsc on 2012-04-08
Apparently such plugin no longer exists, for a few years already, about 2010 I guess.

That's a shame. I've played a bit with GTKmorph, and the interface can really make anyone crazy, but the backend (libmorph) seems powerful, I liked the results. I don't know if it's the GUI part or libmorph part but the actual mesh-editing part was quite nice, albeit I imagine that on more powerful software perhaps you can simply draw "homologue" lines rather than manually edit the homologue points of both  meshes.



GAP (Gimp Animation Plugin) apparently also does "fake morphing" anyway, but that's not the same thing. And speaking for myself, I've found that just about as counter-intuitive, if not more. Perhaps more, I didn't manage to do any animation if I recall, albeit I never looked for manuals or tutorials anyway. With some programs (like the old autodesk animator and fantavision) I used to be able to figure how to do such things intuitively, so I don't have that much patience to decypher manual syntax. I think it has past the time to start writing manuals in a somewhat dumbed-down way, "how to" style. But perhaps there's some "pattern" that makes the standard manuals more intelligible than they seem to be, and I just didn't get it yet. Enough with ranting.

---

