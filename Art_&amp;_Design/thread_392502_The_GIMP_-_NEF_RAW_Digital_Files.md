---
title: "The GIMP - NEF RAW Digital Files"
date: 2007-03-24
forum: Art &amp; Design
---

### Post by Ted_Smith on 2007-03-24
Losing the will to live! 

I want to get The GIMP to read raw NEF files from my Nikon digital camera. I need to install ufraw apparently. So I downloaded that and tried to install it. In order to use that though I needed to install GTK. So I tried. In order to install GTK I needed to install Cairo, Pango, glib, and atk in a specific order (it seems). And not using debs either - compling them all from source. 

I managed to install glib and Pango but atk and Cairo said they needed a higher version of glib to be installed so I didn't get any further than ./configure. But I had installed the latest version from the FTP site? So eventually I gave up after spending 1.5 hours on it! 

Surely there's an easier way to get The GIMP to read RAW data files?  Is it not built into the GIMP yet and if not, is there plans to do so in this modern day of digital photography?

---

### Post by heimo on 2007-03-24
Use Synaptic or aptitude to install gimp-ufraw. Works for me, no hassles. Just used Gimp to import nefs.

```
sudo aptitude install gimp-ufraw
```

---

### Post by Ted_Smith on 2007-03-24
Great! I did not realise it could be doe like that. How did you know that? 

That said, having installed it, I now get : 

```

GTK Accessibility Module initialized

LibGimpWidgets-ERROR **: file gimpstock.c: line 65 (icon_set_from_inline): assertion failed: (pixbuf)
aborting...
Aborted

```

when trying to run GIMP. Any ideas?

---

### Post by heimo on 2007-03-27
Hi, sorry for delay. Did you solve the problem? I'd probably try to remove gimp and gimp-ufraw completely and reinstall. I have no clue what the error message is about. :( I've been using ufraw (and dcraw on which is relies) for about 1,5 years - I always look at the official repositories first for any software: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by philY on 2008-01-20
UFRaw doesn't have any support for brand new nef files that are used by Nikon d300, d3. I opened black pictures. It sucks. I do not know what to do. I found some soft Bibble Lite, it is not free ($69), but it works very slowly. If I have no other choice probably I will buy it anyway. Other disadvantages are as follows:
1. generates really huge tif files, example raw (11MB )and tif is 75MB). It is hard to work with 75MB.
2. It freezes.
----------
Hope Gimp developers would create some plug-in. Another thing is Gimp works only with 8bits, Nikon nowadays creates 12 and 14bits files. Gimp needs to be updated. OK, actually we do not need so many bits, but some ad agencies want to have it, so do their clients. I have not used windows since 2002. 
----------
Greetings
philY

---

### Post by idokus on 2008-06-22
if the newest version of ufraw does not compatible with D300 or D3 you should file a bug/feature request for that package. we're a half year further along so perhaps retry, possibly someone else has filed that bug and its fixed.

same goes for the gimp problems with 12/14 bits and tiff files. Actually if you want to edit images using contrast stretching and diminishing, you want more bits than you can actually see, so you get less artifacts.

hope it helps

---

### Post by idokus on 2008-12-17
Is it perhaps possible to switch to picasa? I've heard they are pretty good with raw files.

I don't know about its bituse... Or if it supports D300- D3- NEF (it does D40 NEF)

picasa is available for linux. See [picasa.google.com/linux/]("http://picasa.google.com/linux/")

---

### Post by jedimasterk on 2008-12-18
Yeah Gimp is really a Photoshop competitor. Adobe supports these newer cameras already!.

---

### Post by kayosiii on 2008-12-19
JedimasterK.... That is not even remotely a helpful comment. Adobe have a much easier time getting necessary implementation from camera manufacturers - so they don't have to reverse engineer every format in the way that the DCRaw developer does.

Picassa also relies on DCRAW for it's raw conversions so it won't work if ufraw does not work.

Things you can do
1) check up on the DCRAW site to see if there is any news on your raw format being reverse engineered.
2)Check if the raw conversion software that shipped with your camera (If you recieved that worked) - This works really well for me (Sigma DSLR). 

3) Adobe have a free tool for converting raw files to DNG files - check and see if you can get that to work under wine. Latest Version of Digikam can deal with DNG files.

4) Investigate commercial raw conversion software for linux out there - somebody mentioned bibble LightZone [http://www.lightcrafts.com/linux/index.html](http://www.lightcrafts.com/linux/index.html) might be another option.

5) see what you can do with a virtual machine.

---

### Post by kayosiii on 2008-12-19
Update - I checked Dave Coffins Site (DCRaw main developer) and support for the nikon d3 and d300 is in so if it is not already supported I would expect to see it in the next version of UFraw. :)

---

### Post by shangjay on 2008-12-19
i'm find it too.:lolflag:

---

### Post by VeeDubb on 2008-12-21
> **jedimasterk said:**
> Yeah Gimp is really a Photoshop competitor. Adobe supports these newer cameras already!.

Photoshop may support those, but they haven't supported them for long, and both cameras were out for quite a while before there was any support from adobe.  Ufraw will follow along soon.



However, as a professional photographer ( [www.stevecoonsphoto.com](www.stevecoonsphoto.com) ) I don't recommend using gimp OR photoshop for raw files.  Both of those programs are intended to in depth image manipulation, not for processing raw files.

There are a variety of dedicated programs for processing raw files, and almost all of them are better than using gimp or using photoshop.

I use Bibble Pro from [www.bibblelabs.com](www.bibblelabs.com) and find that it does an absolutely spectacular job with raw files.  It's $89 for the non-pro version and $130 for the pro version.  (or something like that) and comes in a native linux version.  And I mean NATIVE.  It's not a java app with a linux script to start it up like the linux version of lightzone.

My workflow, whether doing a single portrait or a wedding shoot with 1,500 shots, is as follows:

dump them all in a folder on my desktop

do all my adjusting in Bibble Pro.

Start a batch job to convert them all to high quality, low compression jpegs.

For large photo shoots with multiple cameras and overlapping file names, I use bibble's download batch feature to copy them into a new folder with consecutively numbered file names.

For single portraits that will require a lot of "photoshopping" I use bibble to do basic adjustment, and then save as a tiff.  Then I'll do all my photoshopping using Gimp (yeah, professional photographer, and I use gimp over photoshop)and only when I'm done with all image adjustments do I save in jpeg, so there is an absolute minimum amount of degradation to the image.




I know that a lot of people like to have 100% foss software, but the simple fact of the matter is that there will always be niche markets where it's better to use commercial software.  To me, processing raw files is one of those niches.


On a side note, it's always bugged me that photoshop is called PHOTOshop.  There is absolutely nothing photoshop has over gimp that a photographer needs.  If you need layer styles and all of the other junk that photoshop has, you are NOT a photographer.  You're a graphic designer with a camera.

---

### Post by kayosiii on 2008-12-22
> **VeeDubb said:**
> On a side note, it's always bugged me that photoshop is called PHOTOshop.  There is absolutely nothing photoshop has over gimp that a photographer needs.  If you need layer styles and all of the other junk that photoshop has, you are NOT a photographer.  You're a graphic designer with a camera.

16bit per channel support sure would be nice though.. I would be using the gimp at least twice as much if it was.

Also just noting that prices on Bibble have dropped to 90 and 160(pro)... My camera though is not supported. though it does look nice

---

### Post by alex.rayu on 2008-12-22
Gimp has a plugin that interacts with another RAW package and it imports from RAW.

---

### Post by VeeDubb on 2008-12-28
> **kayosiii said:**
> 16bit per channel support sure would be nice though.. I would be using the gimp at least twice as much if it was.

Also just noting that prices on Bibble have dropped to 90 and 160(pro)... My camera though is not supported. though it does look nice

You know, I agree with that in certain situations, but I've got to be honest, I really don't find a need for 16bit color as a professional wedding photographer.

The images are getting sent to clients who ultimately want 8-bit jpegs that they can have printed at costco or walmart.  I use bibble pro for 99% of my post processing, which handles the full color space of my images just fine.

In the rare event that I need to do serious photo-shopping, it's usually going to be saved in 8-bit jpeg when I'm done, so I'll just export from bibble as an 8bit tiff, and keep it in that format until I'm done editing so i don't loose quality from compression.

8bit color means that there are already almost 17 million possible colors.  It's a rare situation that the human eye is going to be able to find artifacts because the "right" color couldn't be approximated well out of 17 million possible choices.

Now, don't get me wrong.  There are still those VERY rare situations where I would really like to have a larger color space, but I have made 20x30" 300dpi images with gimp, and not been able to detect and color artifacts.

---

### Post by jezebel on 2009-02-14
Thank you, Alex.

I found this thread while searching for a solution to my own problem, and yes, for me, (using the D50), as per Alex's information, this did the trick:

(in Terminal)
sudo aptitude install gimp-ufraw

Now I'm able to open and edit RAW .nef files in GIMP 2.6

Thanks very much.

J.

---

### Post by AJB2K3 on 2009-02-15
> **jezebel said:**
> Thank you, Alex.

I found this thread while searching for a solution to my own problem, and yes, for me, (using the D50), as per Alex's information, this did the trick:

(in Terminal)
sudo aptitude install gimp-ufraw

Now I'm able to open and edit RAW .nef files in GIMP 2.6

Thanks very much.

J.

Yes but the problem still stands, that you cannot edit in 16bit mode.

Anyway just to make a point that for most people weather its 8bit of 16bit images will aether look good or look crap. The average point and shoot person won't have the foggiest idea what the point of raw is and 99% just want a tool to resize/crop/lighten images.

---

### Post by Peter76 on 2009-02-15
Ufraw and so gimp-ufraw edit in 16 bit, you can do all your raw processing in 16 bit and then export to gimp a high quality jpeg to work on in 8 bit

---

### Post by graphius on 2009-02-18
I just want to throw in RawTherapee (available in the repos)
I find a stand alone raw processor much more useful than a plug-in. and yes it handles 16-bit. I did not find any advantage of Bibble over the FREE RawTherapee. In fact for my RAF files it did a better job, especially in the shadows.

Just my .02

PS, you can read about my workflow on my [blog]("http://klughammer.blogspot.com/2009/02/open-source-software.html")

---

