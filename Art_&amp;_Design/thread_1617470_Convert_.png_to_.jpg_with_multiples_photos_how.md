---
title: "Convert .png to .jpg with multiples photos how?"
date: 2010-11-09
forum: Art &amp; Design
---

### Post by Stray Wolf on 2010-11-09
I'm using digiKam and it has batch processes but not one for converting .png to .jpg (that I see).  Does anyone know of a way to convert multiple photos (consecutive and nonconsecutive)?

---

### Post by earlycj5 on 2010-11-09
I use mogrify for stuff like this.

```

man mogrify 

```

as an example

```

mogrify -format jpg *.png

```

See &#8203;&#8203;[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php) for further information.

---

### Post by mcduck on 2010-11-09
I agree that Imagemagick is a great way to do this. (of course you need to install it, which the above post forgot to mention... ;))

If you prefer a graphical tool instead, you should try Phatch, nice & simple tool for batch processing of images. It doesn't pack all the power of Imagemagick but includes all the most commonly used stuff.

..and there's always the Nautilus Image Converter, which adds basic image conversion tools to right-click menu of your file manager.

All these are of course available from the repositories. :)

edit: also if you go for Imagemagick, be careful with *mogrify*. It will overwrite the original images. Use *convert* instead if you want to keep the originals intact and instead wish Imagemagick to create new images for you.

---

### Post by earlycj5 on 2010-11-10
> **mcduck said:**
> I agree that Imagemagick is a great way to do this. (of course you need to install it, which the above post forgot to mention... ;))

I didn't mention it because I wasn't aware that it wasn't installed by default???  It's on all of my machines, maybe I installed it somewhere along the way I guess.

```

sudo apt-get install imagemagick

```

Since the post that followed mine forgot to mention how. ;)

---

### Post by mcduck on 2010-11-10
> **earlycj5 said:**
> I didn't mention it because I wasn't aware that it wasn't installed by default???  It's on all of my machines, maybe I installed it somewhere along the way I guess.

```

sudo apt-get install imagemagick

```

Since the post that followed mine forgot to mention how. ;)

I guess that makes us even then :D

It's not included in the default install, but it's very commonly used and many other apps will bring it along as a dependency so it probably ended on your system that way.

---

### Post by Stray Wolf on 2010-11-10
Thanks for the variety of options!  I'll get right on checking them out.  I'm also going to keep playing in digiKam...I'm sure there's a way!

---

### Post by tg3793 on 2010-11-19
Hello guys. I actually made a [new post here]("http://ubuntuforums.org/showthread.php?p=10134713") since my question was specifically about scripting. However as a couple of you sound pretty knowledgeable regarding command line image editing I wanted to throw this question out to you.

The script I am working on (to rotate images) is using jhead and jpegtran for the command line stuff. The reason I am using two different command line image editors is I can't seem to find one that does what I'm looking for well.

Ideally I would just like a command line program that did one thing well "Rotate Images" but with the additional consideration of NOT changing the modified date/time stamp of the .jpg in question.

Thank you for any help you might be able to give.

---

### Post by katmal on 2010-11-21
Hey take a look at this software,
[http://www.bestsoftware4download.com/software/t-free-imagicon-download-zcvfhpdg.html](http://www.bestsoftware4download.com/software/t-free-imagicon-download-zcvfhpdg.html)

---

### Post by SeijiSensei on 2010-11-21
Here's a scriptable way to restore the timestamp on a file:

```

FILE='somefile.png'
TS=$(ls -l $FILE --full-time | awk '{print $6 " " $7 " " $8}')
mogrify -rotate 90 $FILE
touch $FILE --time="$TS"

```

This obtains the extended timestamp on a file and stores it in an environment variable.  At the end the file is "touched" with the old timestamp.

---

### Post by ngrieb on 2010-11-22
Phatch: Photo Batch Editor. Love this thing! :D
not only will it convert but it can crop, scale, create
alpha channels, colorize, etc...etc...on a photo batch.

---

### Post by hundred1906 on 2010-12-04
Does anyone know how to make Phatch retain the input directory structure for its output?

---

### Post by nagubhai on 2011-10-31
> **earlycj5 said:**
> I use mogrify for stuff like this.

```

man mogrify 

```as an example

```

mogrify -format jpg *.png

```See &#8203;&#8203;[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php) for further information.


Thanks its a nice package////

---

### Post by nagubhai on 2011-10-31
> **nagubhai said:**
> Thanks its a nice package////

Here is the code for mogrify

```
mogrify -format jpg '/home/nagesh/Pictures/Pix/*.png'
```

---

### Post by garryburks on 2011-11-18
There are many photo editing softwares which are capable of doing this - BATCH PROCESS.

---

### Post by Colonel_Ingus on 2012-02-15
> **ngrieb said:**
> Phatch: Photo Batch Editor. Love this thing! :D
not only will it convert but it can crop, scale, create
alpha channels, colorize, etc...etc...on a photo batch.

Exactly what I needed, thank you.

---

