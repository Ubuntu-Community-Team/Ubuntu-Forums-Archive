---
title: "Hugin not working like expected"
date: 2011-07-24
forum: Art &amp; Design
---

### Post by JonasDK on 2011-07-24
Hello everyone

I have a problem with [Hugin]("http://hugin.sourceforge.net/"). I used to have it on my Ubuntu 10.04 and it was working perfectly, but now I've upgraded to 11.04 and installed it using the Software Center it does not preform well. I have added an example here. These are the three pictures I started with:

[LIST]
[*][http://i56.tinypic.com/2laggie.jpg](http://i56.tinypic.com/2laggie.jpg)
[*][http://i52.tinypic.com/dgvlw.jpg](http://i52.tinypic.com/dgvlw.jpg)
[*][http://i53.tinypic.com/28w9ih.jpg](http://i53.tinypic.com/28w9ih.jpg)
[/LIST]
And this was the result: [http://i51.tinypic.com/2a8m33o.jpg](http://i51.tinypic.com/2a8m33o.jpg). As you can see, I expect a little distortion but this is way off. What went wrong? Can anyone create a good panorama with these three pictures? There wasn't really anything wrong with my control points.

I hope anyone with experience with Hugin dwells around here, because they don't have any forum. I've just added this panorama as an example. Hugin has created OK panorama's as well. On my previous installation I used autostitch but it isn't needed anymore with the installation I have apparently. Is that the problem?

Thank you very much,
Jonas

---

### Post by sectshun8 on 2011-07-24
Can't help you much with Hugin... but I got Photoshop CS2 running on my Natty machine here and did a quick Photomerge... I'm guessing this is the effect your trying to get with Hugin... or did you mean to have a super wide completely wierd image?

---

### Post by pommie on 2011-07-24
Just done the pano, you have chosen a complicated stitch for the autostitch function and it cannot do it, its making a horizontal pano instead, you have to manually put in the reference points yourself, I used about eight per image pair and it did a surprisingly good job.

Cheers David

---

### Post by 23dornot23d on 2011-07-24
Used Hugin ..... [[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img97.imageshack.us/img97/5119/huginenhances.jpg") (slight kink in flagpole here)

As said earlier it works on the horizontal .....

[IMG]http://img804.imageshack.us/img804/4839/previewfu.jpg[/IMG]

I just transformed all the photos 90 degrees right and then align and stitched in Hugin .......

Bit of a pain if you have a lot to do but the program works great ...... for free ..... :)

[[COLOR=Red]_***Full Size Finished***_[/COLOR]]("http://img109.imageshack.us/img109/9569/1r3rversion2r.jpg") (the flagpole was not quite straight so added a couple more control points to it)

---

### Post by JonasDK on 2011-07-25
> **sectshun8 said:**
> Can't help you much with Hugin... but I got  Photoshop CS2 running on my Natty machine here and did a quick  Photomerge... I'm guessing this is the effect your trying to get with  Hugin... or did you mean to have a super wide completely wierd  image?
 
 I have used Photoshop in the past and used it for quite a long time but  when I discovered Hugin, I found out that photomerge is quite bad in  merging pictures that have a difference in brightness and lightning.  Just as the panorama you made with Photoshop, the shades aren't right.  Hugin merges perfectly and the composition used to be great right  away on my 10.04 Ubuntu. But now it can only get a good composition half  of the panorama's I try to create. So I want to continue using Hugin  since it is free also. :)

> **pommie said:**
> Just done the pano, you have chosen a complicated  stitch for the autostitch function and it cannot do it, its making a  horizontal pano instead, you have to manually put in the reference  points yourself, I used about eight per image pair and it did a  surprisingly good job.

Cheers David

It seems like my Hugin can do the control points perfectly. No real  problems there. One thing that I've noticed is that Hugin places control  points while putting each photo upside down. But at least the points  are correct so that's not really an issue.
> **23dornot23d said:**
> Used Hugin ..... [[COLOR=Red]_***SCREENSHOT***_[/COLOR]]("http://img97.imageshack.us/img97/5119/huginenhances.jpg") (slight kink in flagpole here)

As said earlier it works on the horizontal .....

[IMG]http://img804.imageshack.us/img804/4839/previewfu.jpg[/IMG]

I just transformed all the photos 90 degrees right and then align and stitched in Hugin .......

Bit of a pain if you have a lot to do but the program works great ...... for free ..... :)

[[COLOR=Red]_***Full Size Finished***_[/COLOR]]("http://img109.imageshack.us/img109/9569/1r3rversion2r.jpg") (the flagpole was not quite straight so added a couple more control points to it)

That looks about right! What version of Hugin do you have? Maybe I'll install it directly from the Hugin site instead of from the Software Center... Because I don't have that little 'Overview' window. The preview mode is actually getting on my nerves, mostly it shows a black screen with a very tiny version of the panorama. Performance isn't that great either.

I let Hugin place the control points (which are good) but it fails at choosing a projection method. The only good projection is called 'Trans Mercator' for this tree-panorama: [Result]("http://i51.tinypic.com/2dv7als.jpg"). But I have had to pick the projection manually. Odd that Hugin can't see that the projection it chooses is way off.

---

### Post by JonasDK on 2011-07-25
Ok so I have updated my Hugin with Autostitch since I had that on my previous installation as well. And it does a WAY better job at selecting control points. When it opened up the preview it looked the same way as my first panorama (the stretched out panorama) but the only thing I had to do was move the picture lower. It had chosen Equirectangular as projection but Rectangular looks perfect! The autocrop works off the picture nicely. So instead of relying on Hugin to finish off the job on itself I'm just going to pay more attention creating each panorama myself and then let Hugin process it in batch after I have set everything up.

This is fixed for my part. :)

---

### Post by 23dornot23d on 2011-07-25
Good to hear ..... that it solved your problem ..... 

I too found the control points were correct and the second picture was flipped upside down too
for the vertical panorama ..... but as said it works ..... in the horizontal .... maybe the developers need
to tweak the program for vertical panoramas as everything else seems to be ok.

I am running the latest repositories from Oneiric 11,10 ...... 
so the latest Hugin version you see was pulled in from there.

Glad the latest one is good for you too I find it to be very quick now ....

If you would in the Threads Tools top right mark it as solved please ..... as people sometimes search for solved results in google ....

---

