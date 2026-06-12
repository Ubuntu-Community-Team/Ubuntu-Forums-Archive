---
title: "A batch job compatible Photo manipulator"
date: 2009-12-21
forum: Art &amp; Design
---

### Post by pajoohesh on 2009-12-21
[COLOR="Blue"]Hi Folks,

I am looking for a software (Open source preferred) such as Picasa to be able to resize or rename and edit multiple pictures as a batch job.

Then I want to be able to upload it in to the internet and share with others.

Any better options that picasa?

Regards,[/COLOR]

---

### Post by kostkon on 2009-12-21
You could try Phatch.

---

### Post by pajoohesh on 2009-12-21
> **kostkon said:**
> You could try Phatch.

Merci Kostkon,
Very light and good software but lacks documentation and image viewer. 

I want to preserve the quality as much as possible. It seems to be slower than Picasa, maybe the quality is more preserved.

Other alternatives are welcomed...

---

### Post by stani on 2009-12-21
> **pajoohesh said:**
> Merci Kostkon,
Very light and good software but lacks documentation and image viewer.
Documentation can be found here:
[http://photobatch.stani.be/documentation/](http://photobatch.stani.be/documentation/)

---

### Post by pajoohesh on 2009-12-22
Thanks stani. 

Is gimp capable of scripting, say to resize group of pictures?

---

### Post by t3h_g3n3r4l on 2009-12-24
[http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)

The GIMP can do it, you just have to create a script of what you want it to do.  I've never worked with enough photos for it to be a significant time-saver over just hand manipulating them, so I've never actually run the batch ops.

---

### Post by garryknight on 2009-12-24
DigiKam has a batch manager that can do the operations you want and more. It can convert, colour auto-correct, rotate, flip, resize, apply a restoration filter, add a watermark, add metadata information, sharpen, and reduce noise, and also rename your file and put it in a new directory. It also has 13 different export options including Flickr, Facebook, SmugMug, Zooomr, Picasaweb, HTML, flash, and iPod.

It's a KDE app so if you're running Gnome, installing it will pull in some KDE libraries.

Actually, on second thoughts, having just looked closer at Gwenview and found much the same options, I realise that all of these functions are provided by the Kipi plugins in KDE 4.3 So you'd need to be running an up-to-date Ubuntu to use them.

---

### Post by doncristobal on 2009-12-27
The gThumb image viewer (package name: gthumb) has some basic batch conversion abilities. 

And of course you could use ImageMagick to write a script, e.g. with Perl and PerlMagick. But this definitely does not include an image viewer. 

I don't know if there's a program that can directly upload pictures to a web service.

---

### Post by AJB2K3 on 2009-12-27
My vote goes to stani's phatch as its so simple to do batch work.
Gimps require learning a programming language.

---

### Post by Newfoundlander on 2009-12-27
For resizing multiple images, I use Nautilus Image Converter.  After installing, just right-click on the image(s) and select "Resize Images".

sudo apt-get install nautilus-image-converter

---

### Post by pajoohesh on 2010-01-13
Hi There,

I've tried different softwares in the meantime and the conclusion up to now is this:
digiKam does not work on my gnome and no idea why. simply it does not show any picture.

Other softwares mentioned here tried but I found Xnview MP as the ultimate solution. it is capable of showing histogram for different channel and also showing customized EXif data, even in the full screen. Besides it has a batch rename option that works. The only lack is the batch processing, in which the windows version has it. 

Hope to see an update soon and solving the batch processing and shell extension as the windows version does that.

For now I use "mogrify" tool (imagemagick) for batch resiszing :
```
mogrify -resize 800x600 *.jpg
```

---

### Post by Xebec on 2010-02-13
> **Newfoundlander said:**
> For resizing multiple images, I use Nautilus Image Converter.  After installing, just right-click on the image(s) and select "Resize Images".

sudo apt-get install nautilus-image-converter
Had absolutely zero effect on my Nautilus. And yes, I did restart it.

---

### Post by Xebec on 2010-02-13
It's a shame that Ubuntu still does not have simple GUI-based batch image converter installed by default.

---

### Post by pajoohesh on 2012-06-26
nautilus-image-converter works perfect on 12.04. Nice job

---

### Post by overdrank on 2012-06-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

