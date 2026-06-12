---
title: "photo stitch in ubuntu"
date: 2007-05-03
forum: Art &amp; Design
---

### Post by pecoronas on 2007-05-03
what is the state of the art in photo stitching (that is joining multiple pictures in a single panoramic picture) in linux?
on win, i used "photo stitch", a tool provided with my canon digital camera, that does everything by itself once you have selected the photos to join and ordered them from left to right. is there anything similar for ubuntu? i know about hugin and enblend but is there something simpler to use? i mean something you just feed with the pictures and does everything by itself? moreover, it seems that photostitch cant run under wine...

---

### Post by brian j on 2007-05-03
There's a plug-in for The Gimp called Pandora that makes Panoramas.
You'll have to use the Synaptic Package Manager (System/Administration/Synaptic Package Manager), Then type Pandora using  Search. When you find Pandora just click the box to install into gimp.

Hope this helps.

---

### Post by slimdog360 on 2007-05-03
there is much better utils then pandora, though it is still a great plugin or certain things.
[http://panotools.sourceforge.net/]("http://panotools.sourceforge.net/")
[http://hugin.sourceforge.net/]("http://hugin.sourceforge.net/")
[http://enblend.sourceforge.net/]("http://enblend.sourceforge.net/")
check out the links in each page for heaps more programs, tutorials etc.
note: if you use hugin you should also use enblend.

---

### Post by pecoronas on 2007-05-03
i'm trying both pandora in gimp and hugin and can't get them to work, it seems i have to set parameters before seeing the results i get applying those parameters :O i'll try a little more, pandora seems fast and easy, but that "overlap" setting has to be... guessed without seeing the actual pics

---

### Post by regomodo on 2007-05-03
Autopano is by far the easiest Panorama app i've ever used. Much better than Photoshop CS2's tool.

[http://en.wiki.autopano.net/Lastest_Beta](http://en.wiki.autopano.net/Lastest_Beta) (yeah, i didn't spell that word wrong)

If you want total control PTAssembler (a gui for Panotools i believe) is very good. Not sure if it's on Linux but i'd be surprised if it wasn't.

---

### Post by pecoronas on 2007-05-03
i see an autopano-sift in my synaptic. is it that? is it a stand alone program or this "sift" means it is a plugin or something?

---

### Post by regomodo on 2007-05-03
> **pecoronas said:**
> i see an autopano-sift in my synaptic. is it that? is it a stand alone program or this "sift" means it is a plugin or something?

Errm. Can't honestly say. I'm using XP atm and i've only used Autopano in windows. If it's the same in linux as it is in windows then i can't see any problems

The debian installer is [http://ftp.autopano.net/releases/AutopanoPro_131Alpha2_050307.deb](http://ftp.autopano.net/releases/AutopanoPro_131Alpha2_050307.deb)
Thats definetly Autopano and should install fine

---

### Post by regomodo on 2007-05-03
Forget Autopano if you wan't a free app. It's shareware. I forgot about that.

Just installed it in Feisty no probs. However, if i was to put a value on it's worth i'd say ~£10 ($20) possibly even a little more.

---

### Post by pecoronas on 2007-05-03
yes you're right, i've tested it and found it's the only "user friendly" app for doing stitch available for linux, unfortunately registration costs $99 and i'm not going to buy it, nor cracking apps in ubuntu, which would be paradoxal. i'll probably use my xp partition with my beloved photostitch for doing it, until i learn how to use pandora, or wine will be able to run photostitch :(

---

### Post by anantmishra on 2007-07-18
Came across this article in linux format (lxf95 August 2007). It says fotox can do a wonderful job of stitching. Find the home of fotox at [http://kornelix.squarespace.com/fotox](http://kornelix.squarespace.com/fotox). I need to try it myself.

---

### Post by Basotang on 2007-07-28
I also was using Photo Stitch (which came form my Canon) in Windows.
I installed Hugin and enblend. Really worth spending a few minutes learning how to use Hugin! The results are excellents, better than in Photo Stitch.  After a few times, it is not much more difficult to use either! Just has to place a few control points...
The thing which is important is to install enblend (otherwise the soft blending option is available in the stitch tab but it does not do anything in fact!)

Seb.

---

### Post by henriquemaia on 2007-08-03
> **anantmishra said:**
> Came across this article in linux format (lxf95 August 2007). It says fotox can do a wonderful job of stitching. Find the home of fotox at [http://kornelix.squarespace.com/fotox](http://kornelix.squarespace.com/fotox). I need to try it myself.

I have tried (just now) fotox and it is useful. Thanks for pointing this out.

---

### Post by gmendoza on 2007-11-19
I just tried Hugin for the first time, and literally created a panorama for the first time in minutes.  The assistant made it very easy, and the results using all default settings were amazing.

After the panorama was created, I used gThumb to crop and compress, but obviously you can use whatever floats your boat.

Highly recommended!

---

### Post by jcornuz on 2007-11-19
In case someone is interested, I have three blog entries on panoramas:

1) [shooting]("http://jcornuz.wordpress.com/2007/11/12/panoramas-1-shooting/")
2) [stitching with Hugin]("http://jcornuz.wordpress.com/2007/11/14/panoramas-2-processing-with-hugin/")
3) [examples]("http://jcornuz.wordpress.com/2007/11/15/panoramas-3-examples/").

meetthegimp.org also has [a video tutorial on the subject]("http://meetthegimp.org/episode-019-paaanoooraaamaaa-and-a-challenge-for-you/").

Take care,

Joel

---

### Post by handaxe on 2007-11-29
@gmendoza

> **gmendoza said:**
> I just tried Hugin for the first time, and literally created a panorama for the first time in minutes.  The assistant made it very easy, and the results using all default settings were amazing.


Did you compile this yourself or use the synaptic deb? I get a seg fault with the std deb.  There is a bug posted from 4/5 months back about this.  So I am curious.  Anyone else have Hugin working under Ubuntu (gnome) Gutsy?

Ta,,
HA

---

### Post by dzidek23 on 2009-09-22
Hi,
for me the best and the easiest software to use is AutoStitch. 

One file windows app which smoothly runs on Wine.

take a look [http://autostitch.net]("http://autostitch.net/")

---

### Post by oboedad55 on 2009-09-23
> **dzidek23 said:**
> Hi,
for me the best and the easiest software to use is AutoStitch. 

One file windows app which smoothly runs on Wine.

take a look [http://autostitch.net]("http://autostitch.net/")

Another one briefly mentioned is Fotoxx. You can get the .deb at getdeb. It has the stitching feature and is very easy to use.

---

