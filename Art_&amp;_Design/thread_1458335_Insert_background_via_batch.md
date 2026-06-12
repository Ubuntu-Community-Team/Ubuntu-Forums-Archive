---
title: "Insert background via batch?"
date: 2010-04-19
forum: Art &amp; Design
---

### Post by Trapper on 2010-04-19
I have a folder of jpg's that are all less than 900x600 in size. I would like to place each of these jpg's on a black 900x600 background. Any way to do this via batch processing in GIMP, Imagemagick, etc?

---

### Post by kaibob on 2010-04-20
> **Trapper said:**
> I have a folder of jpg's that are all less than 900x600 in size. I would like to place each of these jpg's on a black 900x600 background. Any way to do this via batch processing in GIMP, Imagemagick, etc?

Imagemagick convert has a frame option as in the following. However, you specify the width of the frame, which would work if all of your source files are the same size. 

```
convert -frame 20x20 -mattecolor black file.jpg newfile.jpg
```

If the source images vary in size, I think you would have to create a background of the desired size and then use the composite command to put one on the other, as in the following. The file, background.jpg, is simply a 900x600 all-black JPG.

```
composite -gravity center foreground.jpg background.jpg new.jpg
```

You can easily create the background file by applying the following command to any image file (PNG, JPG, GIF). 

```
convert -resize 900x600! -fill black -colorize 100,100,100 source.png background.jpg
```

To batch process with the composite command, a simple for loop would probably be required. Let us know if you need help with this.

---

### Post by Trapper on 2010-04-20
Thanks for all the good info kaibob. I was considering that the Imagemagick composite function was what I'd have to utilize. My images sizes do vary. I also already have the background image. As for looping through all the files, I would like to experiment with that myself before yelling for help. I'll let you know how I fair. I appreciate your assistance.

---

### Post by Trapper on 2010-04-20
I've quickly come to a grinding halt. :)

This is what I have:

background file is /home/trapper/temps/background.jpg

Foreground files are in /home/trapper/transit

pc001.jpg
pc002.jpg
pc003.jpg
etc., etc., etc.

I want to name the new file "foreground file name"ss-900x600.jpg and place it in /home/trapper/transfer

New file name example ... pc001ss-900x600.jpg

Via the commandline this works:

composite -gravity center /home/trapper/transit/pc001.jpg /home/trapper/temps/background.jpg /home/trapper/transfer/pc001ss-900x600.jpg

Obviously, via a loop script I am going to have to set the filename of the current foreground pic in the loop to a variable, do the composite routine and name the newly created file as the foreground filename variable plus ss-900x600.jpg

I can do the composite routine in a loop but I am stumped at creating the foreground filename variable in the loop to name the newly created jpg.

---

### Post by kaibob on 2010-04-20
For right now, to make things easy, copy the background image to the directory that contains the source images. Then, open a terminal window, change to the directory that contains the source images, and enter the following:

```
for file in *.jpg ; do composite -gravity center "$file" background.jpg "${file%.*}ss-900x600.jpg" ; done
```

The above command will create a new copy of the background image. That's OK--just delete it. If this is something that will be used often, you can create a proper shell script with paths and other enhancements.

---

### Post by kaibob on 2010-04-20
I thought I would take this a step further to include paths. I haven't tested the following but I believe it should work.

```
#!/bin/bash

source="/home/trapper/transit"
target="/home/trapper/transfer"
background="/home/trapper/temps/background.jpg"

cd "$source"

for file in *.jpg ; do
   composite -gravity center "$file" "$background" "${target}/${file%.*}ss-900x600.jpg"
done
```

---

### Post by Trapper on 2010-04-21
After reviewing your initial code and doing some research I see where I was attempting to make a mountain out of a mole hill for myself. A learning experience. Thanks for that.

I got your code to work just fine and was able to do hundreds of images quickly. Quite a time saver. Thanks for taking the time to come up with the 2nd offering too. I have not checked it yet but I will give it a try later this AM. It appears to be correct. I'll let you know.

I really appreciate your assistance kaibob. Thank you very much. You've spared me hours of tedious work and have also taught me some things in regards to the code.

Trapper

---

### Post by Trapper on 2010-04-22
kaibob,

```
#!/bin/bash

source="/home/trapper/transit"
target="/home/trapper/transfer"
background="/home/trapper/temps/background.jpg"

cd "$source"

for file in *.jpg ; do
   composite -gravity center "$file" "$background" "${target}/${file%.*}ss-900x600.jpg"
done
```

Works well. Thanks again.

Trapper

---

### Post by kaibob on 2010-04-22
> **Trapper said:**
> I really appreciate your assistance kaibob. Thank you very much. You've spared me hours of tedious work and have also taught me some things in regards to the code.

Trapper

Trapper,

You're most welcome, and I'm glad to hear that the shell script worked properly. Doing things on the command line can be a hassle, but, as you note, they can save a lot of time.

kaibob

---

