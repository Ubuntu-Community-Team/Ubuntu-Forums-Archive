---
title: "Image viewer in B&amp;W"
date: 2009-01-24
forum: Art &amp; Design
---

### Post by tzwrtzis on 2009-01-24
I am looking for an image viewer that can show color pictures in black and white.

It is important for my work flow to select (colored) images while I view them in B&W , ( and I will convert them later on in B&W without viewing the colored version, with more sophisticated methods in gimp)

The only program that I know that is capable of doing so is picasa which is not open source...
gThump can show them in B&W but you have to load them in color and then desaturate them one by one.

[B]
The ideal program would have an option : view all in B&W , with the option of having it always selected.[/B]
DNG RAW format support is welcome but not absolutely required...

The walkaround I am currently doing is to convert a whole folder in B&W and do my review based on those pictures but is not really convenient.

In case my "ideal" viewer does not exist, how is picasa doing in linux?
I had tried it some years ago in windows and it was quite ok for that job.

---

### Post by Sand &amp; Mercury on 2009-01-24
Just out of curiosity, how does seeing them all in black and white help your workflow?

---

### Post by detroit/zero on 2009-01-24
I would imagine that since viewing photos seems to be more than just your hobby, you've already installed ImageMagick. If not:```
sudo apt-get install imagemagick
```This will give you a powerful command-line image manipulation program.

A simple workaround for what you're asking for (until you find a software package that meets your needs, of course) would be to copy the images you wish to view in B&W to a new folder - say, on your desktop - and then convert them all to B&W using the *mogrify* command that comes in ImageMagick:
```
cp -r ~/folder/with/images ~/Desktop
```Then, from what I can see in [mogrify's convert command usage page]("http://www.imagemagick.org/www/convert.html"), it should be as easy as:```
convert -monochrome ~/Desktop/PATH/TO/IMAGE/FOLDER
```This should change all the copied images to a black&white colorscale, and you still have your original images untouched in their original locations. With a little scripting, you could easily automate the process so you don't touch a command line.

It's not exactly what you want, but it's a temporary solution that will work better than what you're currently stuck doing.

Here's the ImageMagick web site:
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

Good luck!

---

### Post by tzwrtzis on 2009-01-24
detroit/zero,

That's what I am currently doing.

I have made a small script that resizes, converts to BW and stores into a new folder all the selected photos with a right click from nautillus.
Thank you very much any way!

___________________________
Here how is it done :


*Installing imagemagick

```
sudo apt-get install imagemagick
```

*Create the batch script.

```
gedit ~/.gnome2/nautilus-scripts/batchBW800x600
```

paste the following text :

```

#!/bin/sh
# Batch resize , desaturate , and store photos in separate directory
mkdir ./BW800x600
for file 
do
name=`echo $file `
  convert -modulate 120,0 -geometry 800x600 -quality 80 $file ./BW800x600/${name}_BW800x600.jpg
done

```

*and make it available in nautillus with right click

```
chmod +x ~/.gnome2/nautilus-scripts/batchBW800x600
```




> **Sand & Mercury said:**
> Just out of curiosity, how does seeing them all in black and white help your workflow?

I'm doing **B&W** photography.

Shooting in color has the advantage of much better post processing 
BUT it is impossible to find out which pictures are interesting while viewing them in color.The selection has to be done in B&W Even seeing them once in color is quite disturbing...

It's just the way I work...

---

### Post by detroit/zero on 2009-01-24
Well, I see you're way ahead of me..

Seems to me that's your best bet until you find what you're looking for.

---

### Post by tzwrtzis on 2009-01-24
:KS

It's just that I don't want to use picasa because:

a) It's not open source althought it's free (as the beer)
b) it's the win version through wine ([http://picasa.google.com/linux/faq.html#24](http://picasa.google.com/linux/faq.html#24)) =;

---

### Post by kaibob on 2009-01-24
The Imagemagick display utility will show color images in black and white. For example:

```
display -monochrome inputfile.jpg
```

Clearly not your ideal program, but if nothing else is available....

---

### Post by graphius on 2009-02-18
This is probably overkill, but I use RawTherapee (available in the Repos) in my workflow (I wrote about that [here]("http://klughammer.blogspot.com/2009/02/open-source-software.html")). In it you can create and save profiles. You could create a profile with low saturation, and set it as your default.
As I said, this may be more than you want, and may end up being less useful than your script...

PS, I have always loved B&W, in fact I was trained in large format B&W, but I do shoot more colour nowdays...

PPS do you have a website of your work?

---

### Post by onthink on 2009-02-19
Still have not found it yet

---

### Post by mcduck on 2009-02-19
Are you using Compiz? In that case you could just use the "Opacity, Brightness and Saturation"-plugin to view any image in black&white with any image viewing program.. ;)

---

