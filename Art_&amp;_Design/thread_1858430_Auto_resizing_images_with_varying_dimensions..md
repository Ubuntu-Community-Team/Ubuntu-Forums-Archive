---
title: "Auto resizing images with varying dimensions."
date: 2011-10-12
forum: Art &amp; Design
---

### Post by Trapper on 2011-10-12
I really don't know what forum to drop this thread in so pardon me if this is the incorrect forum.

I have a _huge_ folder of jpg images that vary greatly in dimensions. I have a situation where no images can be over 900 wide and 675 high. Is there a way (other than manually one at a time) to go through the folder of images, locate all that are larger than 900w and/or 675h and reduce them proportionally to meet the maximum 900x675 parameter? This reduction needs to create the largest possible proportionally resized image inside the 900x675 parameter

I could do this if all images were the same dimensions and were larger than 900x675 but unfortunately that is not the case. There are many oddball sizes and many that meet the parameters in one direction but not the other or vice-versa. There are also square pics. Lastly, the folder also contains many pictures already inside the 900x675 requirement that need to be ignored.

Is there an app or script out there that can handle this?

---

### Post by ofnuts on 2011-10-12
> **Trapper said:**
> I really don't know what forum to drop this thread in so pardon me if this is the incorrect forum.

I have a _huge_ folder of jpg images that vary greatly in dimensions. I have a situation where no images can be over 900 wide and 675 high. Is there a way (other than manually one at a time) to go through the folder of images, locate all that are larger than 900w and/or 675h and reduce them proportionally to meet the maximum 900x675 parameter? This reduction needs to create the largest possible proportionally resized image inside the 900x675 parameter

I could do this if all images were the same dimensions and were larger than 900x675 but unfortunately that is not the case. There are many oddball sizes and many that meet the parameters in one direction but not the other or vice-versa. There are also square pics. Lastly, the folder also contains many pictures already inside the 900x675 requirement that need to be ignored.

Is there an app or script out there that can handle this?ImageMagick's "convert" or "mogrify" commands will handle this. ImageMagick is in your standard repository.

---

### Post by SeijiSensei on 2011-10-12
Imagemagick has a variety of geometry options.  You might find [this document](http://www.imagemagick.org/Usage/resize/) a good starting point.  The "[fill]("http://www.imagemagick.org/Usage/resize/#fill")" option is probably the one you want.

I posted a quick-and-dirty bash script to resize all the images in a directory [here](http://ubuntuforums.org/showpost.php?p=11319092&postcount=11).  Just modify the SCALE variable to fit your needs.

---

### Post by WasMeHere on 2011-10-12
+1 for ImageMagick

It is a great tool for batch work, and the tutorials on the internet are very good

Have fun :-)
Olle

---

### Post by Trapper on 2011-10-12
Wow. This is obviously more complicated to do than I realized. With my lack of knowledge in the area it's probably going to be easier and faster for me to just manually go through the 8000+ images with my viewer/editor, find the ones that qualify for resizing and resize them.

---

### Post by Trapper on 2011-10-12
Well, I "think" I may have figured it out but I am still testing this. It appears to only resize images that are over 900 wide _or_ 675 high, which is what I am wanting.

This is simply run in a terminal from the folder containing the images.


```
$ mogrify -resize '900x675>' *.jpg
```


I will continue testing and post my findings tomorrow.

---

### Post by SeijiSensei on 2011-10-12
I hope you kept backups!  Mogrify overwrites the original images.  I think you have the right syntax, so I'm hoping it all works out well for you!

The script I wrote uses "convert" instead of "mogrify" and stores the resized images into a separate subdirectory to insure that the originals aren't changed in any way.

---

### Post by Trapper on 2011-10-12
> **SeijiSensei said:**
> I hope you kept backups!  Mogrify overwrites the original images.  I think you have the right syntax, so I'm hoping it all works out well for you!

The script I wrote uses "convert" instead of "mogrify" and stores the resized images into a separate subdirectory to insure that the originals aren't changed in any way.

Ha! Yup, I have an understanding of what mogrify does to file and kept a backup of everything I processed.

I did work with your script a bit and adjusted it for my usage. I set the SCALE variable as SCALE='900x675>' 

That does scale my images correctly and places them in the NEWDIR   ..... but it also gives me an original sized copy of all the images that were in IMAGEDIR too. Uniquely, the copies of the original files from the IMAGEDIR are the same dimensions as the originals but the actual file size is a wee bit smaller than the originals. This extra file behavior does not transpire with "mogrify". Perhaps it has something to do with '900x675>'

---

### Post by WasMeHere on 2011-10-12
I'm glad that you are successful with ImageMagick :-)

> **Trapper said:**
> ... Uniquely, the copies of the original files from the IMAGEDIR are the same dimensions as the originals but the actual file size is a wee bit smaller than the originals. This extra file behavior does not transpire with "mogrify". Perhaps it has something to do with '900x675>'

I would keep the original files (maybe move or copy via the shell script) without processing. Otherwise your pictures might be downgraded by a 'lossy conversion'.

---

### Post by Trapper on 2011-10-13
> **Olle Wiklund said:**
> I'm glad that you are successful with ImageMagick :-)

I would keep the original files (maybe move or copy via the shell script) without processing. Otherwise your pictures might be downgraded by a 'lossy conversion'.

Yes, I am keeping the original files rather than the same dimension duplications for that very reason however the behavior of "convert" with this script, as it is, makes me quite reluctant to even use it. It's creating two new images from every one it processes. Well, I have 8000+ images to process. I'm going to end up with the original 8000+ and another 16,000 images. I'm also going to have to make up a function to separate the new created resized images from the newly created same size images.

I'm probably just going to copy the original 8000 to a work folder, run the "mogrify" operation on it and then run a renaming function on the new files.

---

### Post by ofnuts on 2011-10-13
> **Trapper said:**
> Yes, I am keeping the original files rather than the same dimension duplications for that very reason however the behavior of "convert" with this script, as it is, makes me quite reluctant to even use it. It's creating two new images from every one it processes. Well, I have 8000+ images to process. I'm going to end up with the original 8000+ and another 16,000 images. I'm also going to have to make up a function to separate the new created resized images from the newly created same size images.

I'm probably just going to copy the original 8000 to a work folder, run the "mogrify" operation on it and then run a renaming function on the new files.There is a synaxt to assign new names to the ouptut of convert.It's pretty convoluted (on purpose) to just transfer the source file name but once you master it you can avoid the script around the call to "convert".

---

### Post by Trapper on 2011-10-13
> **ofnuts said:**
> There is a synaxt to assign new names to the ouptut of convert.It's pretty convoluted (on purpose) to just transfer the source file name but once you master it you can avoid the script around the call to "convert".


I'm not quite sure what you're getting at here because I've never done renaming with convert but I have used renaming with composite. My basic output syntex for that was in this form:

```
"${target}/${file%.*}-transparent.png"
```

That sent the new file to the "target" dir and renamed it as the original file name plus -transparent.png


However, unless I can resolve my problem of ending up with 2 output files for each input file converted I am simply going to use mogrify for resizing and just run a mass rename on the folder of resized files. Actually I have already done that with copied folder of the 8000 files I am working with and the resizing was successful, as was the renaming.

---

### Post by Trapper on 2011-10-14
Okay, this works with "convert" for me and gives me a _single_ output file from each input file, only resizes files within the SCALE parameters I provided and adds a -resized string to the original file name. abc.jpg becomes abc-resized.jpg, etc.

```
#!/bin/sh
# script to resize images in a directory
IMAGEDIR=/home/trapper/input
NEWDIR=/home/trapper/output
SCALE='900x675>'

cd $IMAGEDIR
mkdir -p $NEWDIR

for file in *.jpg
do
    convert "$file" -resize $SCALE  "$NEWDIR/${file%.*}-resized.jpg"
done
```
Thanks to everyone for their input, suggestions and help in all this.

---

