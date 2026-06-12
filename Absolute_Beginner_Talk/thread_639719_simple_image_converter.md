---
title: "simple image converter"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by pienose on 2007-12-13
I am looking for a simple way to convert .jpg, .png ext to. bmp, something that was in the left click menu in file browser would be very appropriate. I just want something simple, because at the moment I am having to use the Gimp witch is ok but really not very quick and seeing as I need to do ~200 images it's not a very pleasant thing to do. I have looked but can't quite find the thing I'm looking for, but I am sure something must be out there. Thank you very much in advance.

---

### Post by asmoore82 on 2007-12-13
you may wish to use the netpbm tools package: [http://netpbm.sourceforge.net/](http://netpbm.sourceforge.net/)
which is available in the APT Repositories.
However, these apps have no GUI or Graphical Shell Hooks;
But you could convert all of the images in one step by writing a small shell script...

With more details about what exactly you want to do, I'm sure someone
would volunteer up a shell script for you to use.
I would be able to later tonight, but right now I'm at work.

---

### Post by Bert_2 on 2007-12-13
Well, you can use gThumb for that, just select all the files you want to convert, chose extra-> convert format and give in the desired format. Also, gthumb is standard part of ubuntu and I think you can use kview in kubuntu ;)

---

### Post by HermanAB on 2007-12-13
Image magick: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by derjames on 2007-12-13
You can use imagemagick and then create scripts to automate all those tedious tasks... imagemagick is in the repositories and a simple example of automation (picture conversion) is here

[http://www.bit-tech.net/bits/2007/11/26/bashing_through_scripts/4](http://www.bit-tech.net/bits/2007/11/26/bashing_through_scripts/4)

cheers

---

### Post by fenian on 2007-12-13
Imagemagick works well to convert a lot of images.Install it from the terminal with the command...
> 
sudo apt-get install imagemagick

To convert an entire directory from jpg to bmp open a termianl window and navigate to the folder you want to convert(for an example I'll use a folder called pics in the home directory)by typing..

> cd ~/pics

then enter the commmand to convert the files...

>  mogrify -format bmp *.jpg

---

### Post by vanadium on 2007-12-13
People tend to be scared from the command line, but that is really the easiest way for simple, straight-forward conversion:

convert myfile.jpg myfile.bmp

will, yes, convert your jpg to a bmp with 5 seconds typing worf from your part. Remember also the tab key: if you type convert my<tab>, the shell will complete the name automatically.

If you want to convert all files in a directory:

for f in *.jpg; do convert "$f" "$f.bmp" ; done

Imagine doing the conversion with the gimp, opening them one by one.

Only the jpgs that start with "img"

for f in img*.jpg; do convert "$f" "$f.bmp" ; done

---

### Post by pienose on 2007-12-13
> **fenian said:**
> Imagemagick works well to convert a lot of images.Install it from the terminal with the command...


To convert an entire directory from jpg to bmp open a termianl window and navigate to the folder you want to convert(for an example I'll use a folder called pics in the home directory)by typing..



then enter the commmand to convert the files...

thanks that works brilliantly!

How would I convert something like this that could be used as a nautilus script? I just don't want to have to type it out/copy it each time having to cd in and out of files.

also, it's really not a problem, but could this be modified to replace the original file?

Tanks to everyone for the help!

---

### Post by fenian on 2007-12-13
Download the script attached below.Move it to your scripts folder then you need to make some symlinks to make it work for bmp.Do this in a terminal...

>  cd ~/.gnome2/nautilus-scripts/
 ln -s convert_to_png convert_to_bmp

you can change the bmp to other formats and you will be able to conver to those formats.

---

### Post by pienose on 2007-12-14
that dosn't seem to work...or will I need to restart?

---

### Post by svivian on 2007-12-19
> **pienose said:**
> also, it's really not a problem, but could this be modified to replace the original file?
If you convert from bmp to jpg you can delete the bmp files with **rm *.bmp**
Change bmp to be the extension of the files you wish to delete. Make sure you're in the right directory, and that you definitely want to get rid of the original images!

I have a question of my own now. I have a bunch of PNG files, which each have just a few colours and transparent background. How do I convert these to GIF files with white background? Using the -flatten option doesn't do anything. Also can I set the number of indexed colours (eg 16 instead of 256)? I can't find the options...

My current command is:
```
mogrify -format gif *.png
```

---

