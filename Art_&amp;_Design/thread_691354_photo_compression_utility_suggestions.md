---
title: "photo compression utility suggestions"
date: 2008-02-08
forum: Art &amp; Design
---

### Post by showe1966 on 2008-02-08
hi i always have to send lots of photos via the web.

so i take photos with my wizzo digital camera, and have to compress them down to 150-200k each from the photo size of 1.5 megs.

i know there is a neat way of doing this in photoshop, but there is nothing like that in the gimp.

does anyone know of a package for linux that does this ?

if not, i might be prepared to pay a geek or two of you to write me some software to do this.
nothing fancy; in fact, the command line would be better then i can write scripts to run my compressions.

---

### Post by kevinatkins on 2008-02-08
Hi,

You could take a look at some of the various photo management applications available. I know for sure that digikam has a feature to email pictures, automatically compressing them for you; Google's Picasa also has a similar feature..

---

### Post by arigram on 2008-02-08
How about trying out Phatch?
You can do all sort of batch processing to your images with a very comfortable GUI.

[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

### Post by showe1966 on 2008-02-08
i need something open source that works with ubuntu preferrably and will be updated with apt

---

### Post by vanadium on 2008-02-08
```
but there is nothing like that in the gimp
```

Why do you think that? Anyway, besides the options already given, there is also the imagemagicks convert program.

---

### Post by stani on 2008-02-10
> **arigram said:**
> How about trying out Phatch?
You can do all sort of batch processing to your images with a very comfortable GUI.

[http://photobatch.stani.be/](http://photobatch.stani.be/)

In Phatch you can compress your images and even specify the desired size of the jpeg. As Phatch is a new program it is not available through apt in Gutsy. In Hardy however you will be able to install with apt. Now you can install it easily as a deb from the website with gdebi.

Stani

---

### Post by kostkon on 2008-02-10
> **showe1966 said:**
> hi i always have to send lots of photos via the web.

so i take photos with my wizzo digital camera, and have to compress them down to 150-200k each from the photo size of 1.5 megs.

i know there is a neat way of doing this in photoshop, but there is nothing like that in the gimp.

does anyone know of a package for linux that does this ?

if not, i might be prepared to pay a geek or two of you to write me some software to do this.
nothing fancy; in fact, the command line would be better then i can write scripts to run my compressions.

I would use gThumb, it's already installed in your system. Just choose to lower the quality and/or size of the jpegs and then do the batch conversion.

---

### Post by Half-Left on 2008-02-10
Just use GIMP to compress them down using jpg, it give you a preview of the filesize as in realtime. Just save as jpg and the box will come up for compression quality.

---

### Post by stani on 2008-02-10
> **showe1966 said:**
> 
nothing fancy; in fact, the command line would be better then i can write scripts to run my compressions.
In Phatch you can first create and save an actionlist with the GUI in which you can resize the image and set the target size to 150k in the save action. Let's say you save this actionlist as "resize_150k.phatch". Afterwards you can run phatch from the command line in your scripts and it will run without a gui in the terminal:
```
phatch resize_150k.phatch image_folder
```
Phatch is the only program on linux AFAIK which lets you save jpegs with a predefined image size. (With gthumb, nautilus-converter, imagemagick, etc... you can set the image dimensions, but have no direct control on the image size.) Gimp has a preview with an indication of the file size, but for each photo you will have to open each file individually and to find out with the slider the right quality settings. In Phatch you can process any amount of image files or folders with one click or one command line.

I'm the author of Phatch, so if it doesn't do what you want, just let me know.

---

### Post by bharadwaj on 2008-02-11
thanyou for a use ful post Right now I know how to compress my pictures also

---

### Post by jcornuz on 2008-02-11
Hi there,

I think it depends what you need to do: 
[LIST]
[*]If you just have a couple of pictures to resize and send with the best possible quality, the Gimp with a bit of unsharp mask will give you the best output - but it requires to process each photo separately.

[*]If you have hundreds of pictures to resize, then Phatch is what you need - it will do it automagically for you - but it is not optimized for each different picture.
[/LIST]
Another more technical solution, would be to write a batch script using ImageMagick where you can have a lot more flexibility than Phatch (like calculate parameters for an unsharp mask depending on the start / end sizes of your pictures) at the cost of more complexity for writing the script. See an example [here]("http://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/").

It is all about freedom and choice, right :)

Take care,

Joel

---

### Post by meho_r on 2008-02-11
> **stani said:**
> In Phatch you can first create and save an actionlist with the GUI in which you can resize the image and set the target size to 150k in the save action. Let's say you save this actionlist as "resize_150k.phatch". Afterwards you can run phatch from the command line in your scripts and it will run without a gui in the terminal:
```
phatch resize_150k.phatch image_folder
```
Phatch is the only program on linux AFAIK which lets you save jpegs with a predefined image size. (With gthumb, nautilus-converter, imagemagick, etc... you can set the image dimensions, but have no direct control on the image size.) Gimp has a preview with an indication of the file size, but for each photo you will have to open each file individually and to find out with the slider the right quality settings. In Phatch you can process any amount of image files or folders with one click or one command line.

I'm the author of Phatch, so if it doesn't do what you want, just let me know.

Wow, I've just learned of Phatch and I really like it :D One of the "must have" apps (at least for me). Thanks.

---

### Post by stani on 2008-02-18
> **meho_r said:**
> Wow, I've just learned of Phatch and I really like it :D One of the "must have" apps (at least for me). Thanks.

Thanks! I just released a new version of Phatch and it will be part of Ubuntu Hardy!

---

### Post by joblom on 2008-08-30
Stani.....can't get to your site ( sd-2986.dedibox.fr ) to download phatch.  It tries for a few minutes and then times out.  I really want to give it a try because it sounds perfect for me.

---

### Post by stani on 2008-08-30
> **joblom said:**
> Stani.....can't get to your site ( sd-2986.dedibox.fr ) to download phatch.  It tries for a few minutes and then times out.  I really want to give it a try because it sounds perfect for me.

Yep, I know. My web sponsor is working on it. It will be back, no worries. But if you use Ubuntu, there is no need to download it from the site. Just do:```
sudo apt-get install phatch
```

---

### Post by joblom on 2008-08-30
Thanks bunches, Stani.  I got it and it's fantastic.  Did a couple of test runs and it works great.  Love it!  Now to tackle my thousands of photos....literally.

---

### Post by alecspoons on 2008-09-09
Phatch was the exact thing I was looking for to compress photos before emailing them to my Dad (he only has dial-up).

Thanks - worked like a charm!

---

### Post by vedavrata on 2010-04-08
I use gThumb under Ubuntu Linux.

When i save a JPEG file, i just can specify a Quality (%) but i can not see the old and the new file size, as well can not see the image difference (what i would lose), can't i ?.. 

How to see the both old (original) / new (will be saved) file size of JPEG file?
How to see the both old (original) image / new (will be saved) image simulaneously [in two modes "Fit to half a widnow / fit to half a widnow" and "No fit / no fit (i.e. 1:1 / 1:1)"] to evaluate visual quality ?

---

### Post by mcduck on 2010-04-08
> **vedavrata said:**
> I use gThumb under Ubuntu Linux.

When i save a JPEG file, i just can specify a Quality (%) but i can not see the old and the new file size, as well can not see the image difference (what i would lose), can't i ?.. 

How to see the both old (original) / new (will be saved) file size of JPEG file?
How to see the both old (original) image / new (will be saved) image simulaneously [in two modes "Fit to half a widnow / fit to half a widnow" and "No fit / no fit (i.e. 1:1 / 1:1)"] to evaluate visual quality ?
Use Gimp, and install the "Save for Web"-plugin and you'll get a real-time preview how different options affect the image quality & file size.

---

### Post by vedavrata on 2010-04-13
> **mcduck said:**
> Use Gimp, and install the "Save for Web"-plugin and you'll get a real-time preview how different options affect the image quality & file size.  I installed and tried to use...
File -> Save for Web
But it does not show neither the original file size not the original image. :(

---

### Post by JustLuis on 2010-12-21
Phatch rules! thanks Stani, it really helped out here :p

---

