---
title: "Work with RAW files"
date: 2007-05-23
forum: Art &amp; Design
---

### Post by Keli on 2007-05-23
I am a bit new to Linux and I take a lot of pictures in RAW format, (cr2).
Till now I have work with this files in Photoshop or Lightroom but now I can't find anything in Linux to work in this fileformat.
Is any one there who know what to do?

---

### Post by lyceum on 2007-05-23
GIMP only supports the RAW file types that it has been given access to. Unless there is an extention you would need to convert them to PNG. Sorry.

-edit-

I started using UFRaw recently, and I am very pleased with it.

---

### Post by rsambuca on 2007-05-23
Hi,  it looks like the most used RAW image converter for linux right now is dcraw.  It is a command line utility, but there is a GUI that uses dcraw called UFRaw (which also has a gimp plugin available).

Here is a [[COLOR="Red"]good article explaining[/COLOR]]("http://www.linux.com/article.pl?sid=06/08/01/209226") the above, with links to all of the programs.

---

### Post by maruchan on 2007-05-23
[Raw Therapee]("http://www.rawtherapee.com/screenshots.html") is looking pretty good. [DigiKam]("http://www.digikam.org/") is a nice app too.

---

### Post by graigsmith on 2007-05-24
also try UFRAW. the gimp plugin is one of the easisest.

---

### Post by kayosiii on 2007-05-24
You have a number of choices....

1) rawstudio - this has very good batching commands. decent colour correction tools as well as crop and straighten functions.
2) UFraw - works either as a stand alone program or as a plugin for the gimp. Has excellent colour correction facilities.
3) Digikam - Photomanagement App with a built in editor, converts raw image to 16bit per channel image and lets you edit that.
4) Lightzone - commercial app but Linux version is free as in beer.
5) Raw Therapee - Haven't used...
6) Bibble another commercial tool. From the makers of Noise Ninja.
7) Possibly Krita
8) purhaps you could get away with Photoshop under wine.

As of yet i haven't seen anything that will write changes back to a raw file. So the current workflow is to use one of the above programs to colour correct (if needed) and to convert the file to a 16 bit per channel image for further editing or printing. Raw files store the data at 12 bits per channel so no quality is lost doing this (it just uses a lot more disk space - with most cameras raw uses the equivelent of one channel but I wont get into that here).

General purpose editors that support 16 bit per channel images are Krita, Cinepaint and the editor in Digikam. If you are able to run photoshop under wine this is also an option. 

I hope that helps... as A first choice I would probably try raw-studio or ufraw with Krita

Hope that helps

---

### Post by Oki on 2007-05-25
There is lots of options, take a look at this thread; [http://ubuntuforums.org/showthread.php?t=293798](http://ubuntuforums.org/showthread.php?t=293798)

---

### Post by FinkyStinger on 2007-08-16
> **kayosiii said:**
> 
6) Bibble another commercial tool. From the makers of Noise Ninja.


Bibble and Picturecode are two entirely different companies.

> **kayosiii said:**
> 
As of yet i haven't seen anything that will write changes back to a raw file.


Let's keep it that way. RAW image files should be read only to preserve the original information.

---

### Post by UI-Freak on 2007-08-16
I certainly cannot recommend UFRAW, a clumsy usability disaster. Many free RAW editors are disappointingly complicated and/or clumsy. I miss the commercial quality usability found in several programs that combine total manual control with some automation that saves a lot of TIME!

The best free RAW editor I have seen is RAW Therapee. You really have to know what you are doing, but the algorithms used by the program are top notch. It is a very promising program.

---

### Post by muckblit on 2007-08-18
If ubuntu package maintainers would upgrade, I could view and edit Sigma SD14 raw *.x3f files in digikam, ufraw, gimp-ufraw:

Re: [exiv2] Re: Sigma SD14 dslr raw exif support

Andreas,

First pictures is here : [http://digikam3rdparty.free.fr/TEST_IMAGES/RAW/HORIZONTAL/SIGMA-SD14.x3f](http://digikam3rdparty.free.fr/TEST_IMAGES/RAW/HORIZONTAL/SIGMA-SD14.x3f)

Bob,

your SD14 picture can be displayed properlly under digiKam (thumbnail and under editor using 16 bits color depth) :

[http://digikam3rdparty.free.fr/Screenshots/sigma_sd14_under_digiKam_0_9_2.png](http://digikam3rdparty.free.fr/Screenshots/sigma_sd14_under_digiKam_0_9_2.png)

[IMG]http://digikam3rdparty.free.fr/Screenshots/sigma_sd14_under_digiKam_0_9_2.png[/IMG]

Regards

Gilles Caulier


2007/8/18, Gilles Caulier <caulier.gilles@...>:

    >I sent Gilles my email address because yahoogroups Send Email does
    >not have an attachment feature. We will get vertical and
    >horizontal .x3f's online.

    >I have just told digikam 0.9.1 in kubuntu, KExiv2 0.1.1, Exiv2 lib
    >0.12.0, to load my SD14 cam's flash card folder, with card mounted
    >directly on /media. It loads the folder, shows exif info but no
    >thumbnails. I tell it to View or Edit, and it fails, no crash.

    Update to last stable digiKam 0.9.2, update Exiv2 at least 0.14, libkexiv2 0.1.5 and the most important libkdcraw 0.1.1 (witch is used to decode RAW files)

    More info :

    [http://www.digikam.org/](http://www.digikam.org/)
    [http://www.kipi-plugins.org/](http://www.kipi-plugins.org/)

    Gilles Caulier

---

### Post by UI-Freak on 2007-08-27
I can warmly recommend digiKam as well. However, use it as a combo with RawTherapee that comes with a magnificent colour booster. It is based on LAB colours and is much better than plain saturation. The shadow hightlight feature is also much better in RT.

---

### Post by ShagzModo on 2007-08-28
personally i work with RAW studio available from [www.getdeb.net](www.getdeb.net). works fine with my olympus e-1...

cheers!

---

### Post by jis on 2008-02-11
Rawstudio works much faster than Raw Therapee in my experience, but lacks Raw Therapee's great noise reduction feature (among many other features).

---

### Post by lorand.somogyi on 2008-07-11
I have a short [review]("http://lorand.somogyi.name/2008/06/raw-photo-processing-under-linux/") on the topic.

---

### Post by AJB2K3 on 2008-07-11
I have a fuji using the RAF format and I use gimp and the UFRAW plugin with no issues. Its alot better then the old ufraw plugin.
Oh agreed only read the raw image and never write to the raw file.

I don't like raw studio.

---

