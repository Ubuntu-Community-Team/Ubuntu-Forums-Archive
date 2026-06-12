---
title: "mass conversion from .jpg to .png"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-12-08
i have a bunch of .jpg images that i want to be .png images sitting in one folder.  I was wondering if there was a way to convert all of them at once similar to the way you can use ffmpeg to convert a batch of video files?

if you have a suggestion that is quicker than opening up GIMP and saving them all again, please share.

Thanks in advance.

---

### Post by _simon_ on 2006-12-08
Applications -> Graphics -> gThumb

Locate and highlight all of the images you want to convert.

Tools -> Convert Format

---

### Post by kebes on 2006-12-08
In linux there is a commandline program called "convert" that converts image files, and "mogrify" that is good for converting multiple files. They are probably not installed by default, but are part of the [ImageMagick]("http://www.imagemagick.org/script/index.php") toolset. It's definitely in the Ubuntu repositories, so you should be able to go "sudo aptitude install imagemagick" (or something similar). It may be in the 'universe' repository, so you may have to uncomment that line in  your "/etc/apt/sources.list" file in order to get it to install.

Once installed, just go into the directory you want, and run "mogrify":
```

$ cd dir_with_pictures/
$ mogrify -format png *.jpg

```

Now you will have PNG copies of all JPEG files in the directory.

---

### Post by IYY on 2006-12-08
Actually, I believe Imagemagick is installed by default in Ubuntu.

---

### Post by insub2 on 2006-12-09
Thanks all!

I found a way using GIMPS's GAP

Video > Frames Convert > use the dialogue that appears.

---

### Post by c.dric on 2007-01-01
i've tried to convert .jpg to .png using  the gimp and the images end up being more than 4 times bigger (with the highest compression) ?

is this a bug in gimp or am i missing something ?

---

### Post by c.dric on 2007-01-01
well, i got the same results with mogrify ... my files end up 5 times bigger ... so i can't blame gimp. strange tho

---

### Post by kebes on 2007-01-02
Most JPEG -> PNG conversion will increase the filesize.

The image format that is 'best' depends on the content of the image. JPEG is a lossy compression that is best suited to complex, natural images (like photographs).

PNG is lossless compression. It is best suited to pictures that have large regions of continuous color and sharp boundaries. Things like icons, diagrams, and rasterized vector images look best as PNG, for instance. (Whereas JPEG versions of diagrams usually have very visible compression artifacts.)

If you take a complex image (like most photographs) and convert it to PNG, the filesize will almost always be much bigger. That is because PNG is a lossless high-fidelity format. PNG is basically a bitmap image where redundant information is compressed.


So what you're seeing is entirely normal. Typically converting JPEGs to PNGs is not a good idea, since the filesize increase but you gain no image quality (since the JPEG already threw away information to compress the file). Of course you may need to convert to PNG as an intermediate format (in which case filesize is less of an issue).

Hope that helps.

---

### Post by c.dric on 2007-01-02
Oh i see. Thanks for the info.

(I needed the .png for compiz, it doesn't support .jpg images as wallpapers apparently.)

---

### Post by eggshape on 2007-03-12
you can also 

> sudo apt-get install libvips-tools libvips10c2a

there are a lot of good tools, including batch_image_convert:

> batch_image_convert jpeg:85 *png 

(will convert all png files in directory to jpg images at 85% quality)

---

