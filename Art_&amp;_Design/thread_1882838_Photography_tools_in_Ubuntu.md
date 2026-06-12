---
title: "Photography tools in Ubuntu"
date: 2011-11-18
forum: Art &amp; Design
---

### Post by the-saint on 2011-11-18
I've recently switched back to Ubuntu after using Vista a while.. I have started to experiment with photography and would like to know what are the various tools available for me in Ubuntu for the following activities

1. RAW image manipulation
2. Image post processing
3. Adding custom watermarks
4. Creating HDR images

It would be great to have a single tool do all the above stuff above but wouldnt mind to have multiple tools if they are good.

I have already tried darktable, Fotoxx, shotwell and find these not as good as I want them to be..

Any suggestions from one who is into this already is greatly appreciated.

---

### Post by cbanakis on 2011-11-18
I'm not sure if it has all the features you need.

But I recommend taking a look at Gimp.
It is in the software center.
Very similar to Adobe Photoshop.
A bit less powerful, but FREE

---

### Post by Rodney9 on 2011-11-18
My tools
 1. Raw Studio
 2. Gimp 
 3. Gimp - [http://goo.gl/gzIVq](http://goo.gl/gzIVq)
 4. I haven't used this qtpfsgui - [http://olafsblog.sysbsb.de/creating-hdr-images-in-ubuntu-with-luminance-qtpfsgui/](http://olafsblog.sysbsb.de/creating-hdr-images-in-ubuntu-with-luminance-qtpfsgui/)

There are thousands of Gimp Tutorials on the net - [http://goo.gl/ECpVL](http://goo.gl/ECpVL)

Rodney

---

### Post by Lars Noodén on 2011-11-18
Check Digikam next.

---

### Post by expired_fox on 2011-11-18
1) Darktable
2) Darktable (+ optionally Photoshop via wine. In the near future I will refuse from PS completely, just after Henrik Andersson will finish its local modifications implementation for Darktable.)
3) Darktable
4) Luminance HDR, but I don't like tonemapping results and prefer exposure fusion approach (via enfuse).

---

### Post by garryburks on 2011-11-18
Are you sure Ubuntu has all these features?

---

### Post by ofnuts on 2011-11-18
> **the-saint said:**
> I've recently switched back to Ubuntu after using Vista a while.. I have started to experiment with photography and would like to know what are the various tools available for me in Ubuntu for the following activities

1. RAW image manipulation
2. Image post processing
3. Adding custom watermarks
4. Creating HDR images

It would be great to have a single tool do all the above stuff above but wouldnt mind to have multiple tools if they are good.

I have already tried darktable, Fotoxx, shotwell and find these not as good as I want them to be..

Any suggestions from one who is into this already is greatly appreciated.

[LIST=1]
[*]RAW image manipulation: I use UFRaw
[*]Image post processing: Gimp, but for some general processing on JPEG, the built-in tools of Digikam are OK.
[*]Adding custom watermarks: I tend to avoid that (IMHO: watermark_obnoxiousness = ( photographer_ego / image_quality ) so my own watermarks would be sub-pixel size ;) ) , but Gimp will do it nicely.
[*]Creating HDR images: QTPFSGUI. Using Gimp's GEGL C2G filter can also add a lot of dynamic to an image: [http://www.flickr.com/groups/gimpusers/discuss/72157619079536887/](http://www.flickr.com/groups/gimpusers/discuss/72157619079536887/)
[*]Image management: currently using Digikam but there are some things I don't like in the UI, so I'm considering using Picasa (that's what I used on Windows).
[/LIST]

---

### Post by Jerry N on 2011-11-18
Be warned that GIMP truncates your nice 12 or 14 bit RAW file to 8 bits.  Version 2.8 will allegedly fix that, if and when it is ever released.  

Jerry

---

### Post by bluexrider on 2011-11-18
Here is some useful info:
[http://libregraphicsworld.org/](http://libregraphicsworld.org/)

---

### Post by prokoudine on 2011-11-18
> **Jerry N said:**
> Version 2.8 will allegedly fix that

No, it won't :)
> **Jerry N said:**
> , if and when it is ever released.

Soon, v2.7.4 is nearly out.

@topistarter

darktable, GIMP, Luminance HDR

---

### Post by ofnuts on 2011-11-18
> **Jerry N said:**
> Be warned that GIMP truncates your nice 12 or 14 bit RAW file to 8 bits.  Version 2.8 will allegedly fix that, if and when it is ever released.  

JerryLike every other image editor if you save in an 8-bit/channel format such as JPG or PNG. The problem isn't so much the truncation than the lack of precision in some computations (not much a problem in photography) or the quick appearance of posterization in low lights when try to light them up.

AFAIK,  floating-point Gimp won't be v2.8 but V3.

---

### Post by Jerry N on 2011-11-18
> **ofnuts said:**
> Like every other image editor if you save in an 8-bit/channel format such as JPG or PNG. The problem isn't so much the truncation than the lack of precision in some computations (not much a problem in photography) or the quick appearance of posterization in low lights when try to light them up.

AFAIK,  floating-point Gimp won't be v2.8 but V3.

Even if you have saved in RAW, GIMP truncates the data to 8 bits per color channel before any image manipulation is started.  Photoshop, on the other hand, does 16 bit calculations.  Saving the final result in JPEG will of course result in 8 bits per color but _after_ the image has been manipulated.  If I go to the trouble of saving in RAW format, I certainly want to maintain the best computation precision possible, which means staying with Photoshop.  I thought I read someplace a year or so back that GIMP 2.8 would use 16 bit computation but I could easily be wrong about that.  If the progress on 2.8 is any indication, I will probably be too old to care by the time GIMP 3 is released.

Jerry

---

### Post by robert shearer on 2011-11-18
For colour management....
[http://ubuntuforums.org/showthread.php?t=1868244](http://ubuntuforums.org/showthread.php?t=1868244)

---

### Post by VeeDubb on 2011-11-19
For 1&2 I STRONGLY recommend Bibble from bibblelabs.com

I've been using it for a couple of years now, and it's an amazingly powerful application.  I know it's not FOSS, which rubs some folks the wrong way, but it's reasonably priced and I'm a big fan of supporting developers and software companies that officially support linux.  The one thing I will mention about it, is that the interface is quite a bit different than anything you're probably used to.  Watch some of the demo videos on their website and take advantage of their 30 day trial.  I do 98% of my image editing and processing in bibble.

Watermarks I can't help much because I have an account through zenfolio and do all of my image previewing for clients through my website, which handles the watermarking for me.

As for HDR, I've only played with HDR a handful of times, but I know that Hugin, which was originally just for stitching panoramas, also has an HDR option.


Also, color management was mentioned.  I HIGHLY recommend DispcalGUI.  Argyll is arguably one of the best and most powerful appications out there (free or otherwise) for color calibrating displays.  However, it's a mind bending nightmare to use.  DispcalGUI is a user-friendly but still powerful GUI for Dispcal, which is the display calibration component of the Argyl color management system.

---

### Post by dhor on 2011-11-19
New - old approach to HDR theme - MacroFusion:

[http://ubuntuforums.org/showthread.php?p=11470595#post11470595](http://ubuntuforums.org/showthread.php?p=11470595#post11470595)

---

### Post by ofnuts on 2011-11-19
> **Jerry N said:**
> Even if you have saved in RAW, GIMP truncates the data to 8 bits per color channel before any image manipulation is started.  Photoshop, on the other hand, does 16 bit calculations.  Saving the final result in JPEG will of course result in 8 bits per color but _after_ the image has been manipulated.  If I go to the trouble of saving in RAW format, I certainly want to maintain the best computation precision possible, which means staying with Photoshop.  I thought I read someplace a year or so back that GIMP 2.8 would use 16 bit computation but I could easily be wrong about that.  If the progress on 2.8 is any indication, I will probably be too old to care by the time GIMP 3 is released.

Jerry

16 bits isn't enough either. AFAIK there is no 16-bit Gimp because the author felt they would have to go to floating-point Gimp soon after, so they preferred to make on single big jump (such changes do break a lot of existing plugins/scripts). There are already bits of Gimp (the GEGL tools) that run in floating point.

When you come from Raw, the processing that requires high  bit depth (color/contrast) is done in the RAW processing software or RAW processing plugin (UFRaw can be both) and this is done in high precision. In a RAW-originated workflow, Gimp is used for local doctoring that doesn't require as much precision.

2.8 and 2.10 will be 8-bit. Floating-point is for V3.

---

### Post by Gotlieb on 2011-11-19
Try Photoshop under Wine.. tried it and it works okay for me :)

---

### Post by dhor on 2011-11-20
Why are you using RAW format and GIMP for manipulations? It makes no sense.

The advantage of using RAW format is do as much non-destructive transformations as possible. GIMP with 8bit precission can be used for, let's say, removing spots or red eyes. 

All colour, exposure, blending, highlight saving work you have to do in more advanced apps. Darktable, Rawtherapee, Rawstudio, Photivo, digiKam, BibblePro  - all of them allow you to transform photos with 16/32bit precission. Of course, if we concern about quality. And if we look closest to these apps, it comes out, that they have plenty of filters, almost-layers solutions, sharpening, and so on. And in fact in 95%  we don't need to use any other graphics editor.

---

### Post by VeeDubb on 2011-11-20
> **dhor said:**
> Why are you using RAW format and GIMP for manipulations? It makes no sense.

The advantage of using RAW format is do as much non-destructive transformations as possible. GIMP with 8bit precission can be used for, let's say, removing spots or red eyes. 

All colour, exposure, blending, highlight saving work you have to do in more advanced apps. Darktable, Rawtherapee, Rawstudio, Photivo, digiKam, BibblePro  - all of them allow you to transform photos with 16/32bit precission. Of course, if we concern about quality. And if we look closest to these apps, it comes out, that they have plenty of filters, almost-layers solutions, sharpening, and so on. And in fact in 95%  we don't need to use any other graphics editor.

I couldn't have said it better myself.

If you're serious about photography, take the best possible image your camera, glass, and skill will allow, then do as much editing as humanly possible in RAW before you load it into another program.  Photoshop is a misnamed program, because it really isn't for photos.

---

### Post by expired_fox on 2011-11-20
> **VeeDubb said:**
> For 1&2 I STRONGLY recommend Bibble from bibblelabs.com

I've been using it for a couple of years now, and it's an amazingly powerful application.  I know it's not FOSS, which rubs some folks the wrong way, but it's reasonably priced and I'm a big fan of supporting developers and software companies that officially support linux.  The one thing I will mention about it, is that the interface is quite a bit different than anything you're probably used to.  Watch some of the demo videos on their website and take advantage of their 30 day trial.  I do 98% of my image editing and processing in bibble.

Watermarks I can't help much because I have an account through zenfolio and do all of my image previewing for clients through my website, which handles the watermarking for me.

As for HDR, I've only played with HDR a handful of times, but I know that Hugin, which was originally just for stitching panoramas, also has an HDR option.


Also, color management was mentioned.  I HIGHLY recommend DispcalGUI.  Argyll is arguably one of the best and most powerful appications out there (free or otherwise) for color calibrating displays.  However, it's a mind bending nightmare to use.  DispcalGUI is a user-friendly but still powerful GUI for Dispcal, which is the display calibration component of the Argyl color management system.
I have a paid licence of this software. It's quite good, but the open source Darktable is better. I've switched to the DT.

---

### Post by prokoudine on 2011-11-20
> **ofnuts said:**
> 2.8 and 2.10 will be 8-bit. Floating-point is for V3.

Alas, this may be not the case. Last thing I heard from mitch (current project lead) is that due to broken support for input devices in GTK+2 the v3.0 might be just 2.10 in GTK+3. Unless someone is *really* quick with further moving to GEGL.

That's sad, but kinda makes sense, because lack of proper support for Wacom and suchlike makes all great changes between 2.6 and 2.8 in the brush system unusable for most people.

OTOH that makes 2.10 to 3.0 development cycle shorter, **and** work on high bit depth support can be done in parallel.

---

### Post by VeeDubb on 2011-11-21
> **expired_fox said:**
> I have a paid licence of this software. It's quite good, but the open source Darktable is better. I've switched to the DT.

Serious question here:  In what way to you find darktable to be better?  I've found it to be woefully lacking in functionality.  Overall, I'd say it's capable of, at best, half of the functions I would consider 'basic' for post processing raw files.  I think it would be fine if you intended to open each outputted jpeg in a Gimp and continue working on it, but it simply doesn't have the functionality needed to do all of your post in raw.

---

### Post by earlycj5 on 2011-11-22
> **VeeDubb said:**
> Serious question here:  In what way to you find darktable to be better?  I've found it to be woefully lacking in functionality.  Overall, I'd say it's capable of, at best, half of the functions I would consider 'basic' for post processing raw files.  I think it would be fine if you intended to open each outputted jpeg in a Gimp and continue working on it, but it simply doesn't have the functionality needed to do all of your post in raw.

I'd say when I first made the comparison, I'd have agreed with you, but now I find there are features in DT that I miss and I have LR now on my Mac.  I wish that the Mac version of DT weren't so buggy.

I find it far from woefully lacking, it has some tools that LR doesn't. Can't speak to Bibble currently as I've not tried in over a year now...

---

### Post by VeeDubb on 2011-11-22
If you haven't tried bibble in over a year, you haven't tried bibble at all.  The current version, which cam out about a year ago, is a ground-up redesign.  I would say that in many ways it is superior to lightroom, which I find to be buggy and bloated considering how much it costs.

---

### Post by expired_fox on 2011-11-22
> **VeeDubb said:**
> Serious question here:  In what way to you find darktable to be better?  I've found it to be woefully lacking in functionality.  Overall, I'd say it's capable of, at best, half of the functions I would consider 'basic' for post processing raw files.  I think it would be fine if you intended to open each outputted jpeg in a Gimp and continue working on it, but it simply doesn't have the functionality needed to do all of your post in raw.
The only thing I miss in DT is the local modifications (and this will soon be done). But since I'm mostly landscape shooter, I don't need it much.
But on the other hand where the color correction tools in Bibble? They don't even have Lab curves tool, although DT has superior LCh-based one (much better than Lab curves: provides the same capabilities, made it in user-friendly manner).
The shadow recovery plugin I'm developing for DT has no analogue in bible too. I see no way the bible can be better in the near future.

---

### Post by ShodanjoDM on 2011-11-22
GIMP, ofcourse.

For RAW processing, I'm using - depending on the needs and occasions:

- UFRaw
- Darktable
- RawTherapee
- Photivo

Another graphic softwares that I use:

- Luminance HDR
- Hugin
- fotoxx
- Tintii
- SmillaEnlarger
- Geeqie/Gthumb
- Shotwell

---

### Post by earlycj5 on 2011-11-22
> **VeeDubb said:**
> If you haven't tried bibble in over a year, you haven't tried bibble at all.  The current version, which cam out about a year ago, is a ground-up redesign.  I would say that in many ways it is superior to lightroom, which I find to be buggy and bloated considering how much it costs.

Ah, well, considering I paid less for LR (buying from Adobe) than Bibble, I don't think I'll complain. ;)

To be honest, I've not found it buggy at all.

That said, I shall download and try the latest Bibble just to see what I might be missing.

---

### Post by prokoudine on 2011-11-23
> **VeeDubb said:**
> Serious question here:  In what way to you find darktable to be better?  I've found it to be woefully lacking in functionality.  Overall, I'd say it's capable of, at best, half of the functions I would consider 'basic' for post processing raw files.

And the missing basic bits would be...?

---

### Post by VeeDubb on 2011-11-23
> **prokoudine said:**
> And the missing basic bits would be...?

Basic features that should be considered the bare minimum if you want to do all of you post processing in raw that DT lacks:

Heal
Clone
Monitor color profiles
Soft-proofing for print profiles
IPTC metadata
The ability to build, store and apply presets


It's also missing a number of more advanced features that are extremely useful, and found in most commercial equivalents, although not required:

Layered editing
Plugins for simulation of various films and papers
Lens correction

I'm sure there are many others, but those are the ones that come to mind right off the top of my head.  

The whole point of shooting in raw is that it allows you to do far more detailed and deliberate editing and optimization of the image data your camera captures BEFORE it gets stepped down to an 8-bit jpeg.  

If your raw editor can't do all the things I listed and more, you'll end up doing half you editing after export, in which case you may as well shoot in jpeg to begin with and save yourself the time.

---

### Post by prokoudine on 2011-11-23
> **VeeDubb said:**
> Basic features that should be considered the bare minimum if you want to do all of you post processing in raw that DT lacks:

Heal
Clone

Lightroom-like spot removal tool is available since 0.9.0

> **VeeDubb said:**
> Monitor color profiles

Available since 0.4.0

> **VeeDubb said:**
> Soft-proofing for print profiles

AFAIK, available since 0.9.0, but I need to double-check

> **VeeDubb said:**
> IPTC metadata

XMP is available

> **VeeDubb said:**
> The ability to build, store and apply presets

Available since 0.8.0 or so

Out of curiousity, what version of darktable did you last see? 0.3? :)

> **VeeDubb said:**
> It's also missing a number of more advanced features that are extremely useful, and found in most commercial equivalents, although not required:

Layered editing
Plugins for simulation of various films and papers
Lens correction

Lens correction is available too, since late 2009 or so.

You haven't really used daktable any long, have you? :)

---

### Post by VeeDubb on 2011-11-23
XMP is not IPTC.  The absence of IPTC support is a deal breaker all by itself. 

I'm running 0.9-1 from the Ubuntu repos.

While I certainly believe you that those features are burried in there somewhere, if I can't find them within 5 minutes, which I can't, then there is something so fundamentally wrong with DT that it's not worth using.  Maybe it's just a conflict with Unity since the program doesn't have any menus at all.

---

### Post by expired_fox on 2011-11-23
> **VeeDubb said:**
> XMP is not IPTC.  The absence of IPTC support is a deal breaker all by itself. 

I'm running 0.9-1 from the Ubuntu repos.

While I certainly believe you that those features are burried in there somewhere, if I can't find them within 5 minutes, which I can't, then there is something so fundamentally wrong with DT that it's not worth using.  Maybe it's just a conflict with Unity since the program doesn't have any menus at all.
It's strange. I was complete amateur when started using Bibble. Then I saw DT and found it being just plain clearer, very consistent, unlike Bibble, that was the mess. With the DT I know where should I go to do the task. The bibble is inferior in this aspect.

---

### Post by prokoudine on 2011-11-23
> **VeeDubb said:**
> XMP is not IPTC.

I *kinda* know the difference, strange it may seem :)

> **VeeDubb said:**
> The absence of IPTC support is a deal breaker all by itself.

Yes, in certain cases like stock photography or shooting for agencies.

> **VeeDubb said:**
> While I certainly believe you that those features are burried in there somewhere, if I can't find them within 5 minutes, which I can't, then there is something so fundamentally wrong with DT that it's not worth using.  Maybe it's just a conflict with Unity since the program doesn't have any menus at all.

It never had menus and probably never will. Most of the features are in sidebars, implemented as plug-ins whose visibility can be toggled (the management UI is in the bottom right corner).


> **expired_fox said:**
> It's strange. I was complete amateur when started using Bibble. Then I saw DT and found it being just plain clearer, very consistent, unlike Bibble, that was the mess. With the DT I know where should I go to do the task. The bibble is inferior in this aspect.

Um, I don't think it's strange. Us creative folks are quite attached to our tools. You probably won't find a construction worker attached to a chainsaw, but give a copy of Photoshop to a designer and try taking it away after a couple of weeks, and all hell goes loose :)

---

### Post by VeeDubb on 2011-11-24
> **prokoudine said:**
> I *kinda* know the difference, strange it may seem :) 

Yes, in certain cases like stock photography or shooting for agencies.

Yes, for selling stock photos, IPTC is often required.  It is also _the_ standard for photojournalism.  Additionally, if you shoot a wedding or any other professional job and want to provide your client with digital proofs that aren't watermarked, it is strickly IPTC metadata that most photo labs check to make sure they're not printing copyrighted work.  I realize that you or I could circumvent and/or remove the unwanted metadata in a heartbeat, but the average consumer cannot.


> **prokoudine said:**
> Us creative folks are quite attached to our tools. You probably won't find a construction worker attached to a chainsaw, but give a copy of Photoshop to a designer and try taking it away after a couple of weeks, and all hell goes loose :)

I agree with every bit of that, except the idea that a construction worker wouldn't be attached to a chainsaw.  Once upon a time I did construction work, and while my work rarely involved chainsaws, it involved nail-guns every day, and I HATED the Botstich, loved the Porter-Cable.  All craftsmen get attached to their tools, regardless of the craft.  (Don't even get me started on Canon vs Nikon)

Anyway, at the end of the day, I personally find DT to be so cumbersome and unintuitive that I would never use it.  If you feel the same way about bibble, you're equally entitled to that opinion.  The one part of this that I stick to adamantly is that anyone looking for a solution should consider and take advantage of free trials where they're offered.

---

### Post by pixiq on 2011-11-24
I'm new here and I really enjoyed reading this thread. It's so true that you fall in love with your tools, not to mention cars. The discussion is way above my level, obviously there is a lot to learn before I can make really good pictures

0. my camera only saves jpeg files ;-)

---

### Post by lundbech on 2011-12-11
> **the-saint said:**
> I've recently switched back to Ubuntu after using Vista a while.. I have started to experiment with photography and would like to know what are the various tools available for me in Ubuntu for the following activities

1. RAW image manipulation

That's a problem. **BibblePro** not FOSS, but it is the only serious tool for Linux. It's VERY good and compares to the best Win/Mac RAW converters. Awesome set of plugins.

OSS software there's a lot of.

**Darktable**. Very intuitive UI, nice basic set of features but also lacks some. It's new and development is reasonably fast.
**RawTherapee**. Version 3 has been re-designed but the UI is still a mess. Features compare with Darktable.
**Photivo**. Havent used this much but it seems to compare with the two above. UI looks like something from the 19th century! ;-)
**Raw Studio**. Far too few features for more than casual use. Development seems very slow.
**DigiKam**. A Photocollection management tool with raw conversion. Unlike Darktable and Rawtherapee not built for mass conversion of RAW files.

Problem is that there are to many people out there trying to do the same things at the same time. If only they could/would join efforts and build on top of each other, rather that trying to do the same things over and over again.

Bibble is ***the*** serious choice for Linux. But watch Darktable there might be something there in a year or two.


> **the-saint said:**
>  2. Image post processing

GIMP in spite of all the things it doesn't have. There are no alternatives other than Photoshop.

---

