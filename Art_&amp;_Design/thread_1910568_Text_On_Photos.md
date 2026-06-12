---
title: "Text On Photos"
date: 2012-01-17
forum: Art &amp; Design
---

### Post by Momof9Blessings on 2012-01-17
Hi all,

I am using Ubuntu 11.10 (dual boot - never go into windows :) ) and CS5 in Wine!

Ok CS5 cannot do text in wine - that is ok....  it does everything else I need it to do....  

BUT...  I need to put text on things.

I have been using Pinta Image Editor, works ok.  But once you leave the text, you can't go badck and edit it.  I also need to be able to do things to the text, rotate, resize etc (change color).... and it would be nice to do this at anytime....

Here's another problem - I can't use GIMP - something about using the same files as something else.... might be CS5

I also need the program to leave my image as it is... not put it into a letter size paper (libre office), fotomax worked great, but made it do the above....

I do 12x12 digital scrapbooking pages and I am also a designer - so I need something I can manipulate the text....

Thank you for your help!!!

---

### Post by prokoudine on 2012-01-17
> **Momof9Blessings said:**
> 
Here's another problem - I can't use GIMP - something about using the same files as something else.... might be CS5

This is completely undecipherable. Whenever you complain about something, pretty please provide exact quote of what applications are telling you.

Photoshop installed on WINE should never affect native version of GIMP for Linux. You didn't try installing Windows version of GIMP via WINE, did you?

---

### Post by Momof9Blessings on 2012-01-17
I tried to install Gimp via Ubuntu software center(I actually had it installed before I installed CS5 - was using it a bit, but was unhappy with it...I need things from photoshop for my business) (the last update, I remember seeing them taking off gimp stuff)....

I just tried again and this is the message...

"Package Dependencies cannot be resolved...

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

I guess if that can be resolved without messing up CS5 - that is ok too....  But I don't want to mess up CS5.... LOL  I am back to work (off over the holidays, so had time to set up and play with Ubuntu....)  My plan is to NEVER go back to windows....

---

### Post by coffeecat on 2012-01-17
> **Momof9Blessings said:**
> 
I just tried again and this is the message...

"Package Dependencies cannot be resolved...

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

This sounds like a package manager problem, possibly caused by incompatible packages from a 3rd part repository. There really should be no problem in installing GIMP in Ubuntu.

I suggest you start a new thread in General Help focussing on your problem installing GIMP. You need to post that error message, the version of Ubuntu you are using, and details of any respositories you have enabled. If you can manage to install the Gimp, then my guess is that it's your best option for what you want to do. In case anyone has any other suggestions for software for text on photos, I'll leave this thread open, but if you do open a new thread, please confine installing Gimp discussion to that thread, so we don't have parallel support posts in two threads.

---

### Post by prokoudine on 2012-01-17
Which version of GIMP does the software center report to have? Did you try to add any third party repositories (PPA)?

Please try running from terminal:

$ sudo apt-get update
$ sudo apt-get install gimp -y

and post the entire output from the last command here.

---

### Post by Momof9Blessings on 2012-01-17
ok here is what happened...

```
lori@Lori-PC:~$ sudo apt-get install gimp -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: libpoppler-glib4 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

As far as PPA, I have no idea....  I did what they wanted me to do in WINE (on the website to install CS5).... (I had some problems with my first install of ubuntu - so reinstalled it and all was working fine....)  

Thank you :)

---

### Post by BcRich on 2012-01-17
> **Momof9Blessings said:**
> Hi all,

I am using Ubuntu 11.10 (dual boot - never go into windows :) ) and CS5 in Wine!

Ok CS5 cannot do text in wine - that is ok....  it does everything else I need it to do....  

BUT...  I need to put text on things.

I have been using Pinta Image Editor, works ok.  But once you leave the text, you can't go badck and edit it.  I also need to be able to do things to the text, rotate, resize etc (change color).... and it would be nice to do this at anytime....

Here's another problem - I can't use GIMP - something about using the same files as something else.... might be CS5

I also need the program to leave my image as it is... not put it into a letter size paper (libre office), fotomax worked great, but made it do the above....

I do 12x12 digital scrapbooking pages and I am also a designer - so I need something I can manipulate the text....

Thank you for your help!!!
Hi [Momof9Blessings]("http://ubuntuforums.org/member.php?u=593732")
The Gimp 2.6(stable) does not retain edit-ability of text (as a non-rasterized text object) once text has been transformed. Rotation and resizing of text is a transformation. Inkscape on the other hand allows many more options for working with text including retaining edit-ability after transforming text, plus various raster image manipulation options which might be of use for digital scrapbooking such as the effects in the Filters menu. But it is not a raster editing application like Photoshop or the GIMP it's more like Adobe Illustrator (a vector editing program) :)

---

### Post by Momof9Blessings on 2012-01-17
Thank you BcRich!!!

That will work great - what I was looking for!!!  Did not realize it was already installed too!!!

Now I need to find an instruction manual - off to look!

---

### Post by 1script on 2012-01-18
Gimp is obviously great but there are other ways to add text to photos. In fact, depending on what you are trying to do, they may even be vastly more efficient, such as using *mogrify* for example:

```
mogrify -pointsize 16 -fill "rgba(0,0,255,0.3)" -gravity southeast -annotate +5+5 "Copyright 2012 Momof9Blessings" *.jpg
```

which would add *Copyright 2012 Momof9Blessings* to the lower right corner (southeast) of every jpg picture file in the directory.

---

### Post by oldfred on 2012-01-18
Another Fred with many scripts for imagemagick
[http://www.fmwconcepts.com/imagemagick/index.php](http://www.fmwconcepts.com/imagemagick/index.php)

---

### Post by Rebelli0us on 2012-02-14
> **Momof9Blessings said:**
> Hi all,

I am using Ubuntu 11.10 (dual boot - never go into windows :) ) and CS5 in Wine!

Ok CS5 cannot do text in wine - that is ok....  it does everything else I need it to do....  

BUT...  I need to put text on things.

I have been using Pinta Image Editor, works ok.  But once you leave the text, you can't go badck and edit it.  I also need to be able to do things to the text, rotate, resize etc (change color).... and it would be nice to do this at anytime....

Here's another problem - I can't use GIMP - something about using the same files as something else.... might be CS5

I also need the program to leave my image as it is... not put it into a letter size paper (libre office), fotomax worked great, but made it do the above....

I do 12x12 digital scrapbooking pages and I am also a designer - so I need something I can manipulate the text....

Thank you for your help!!!

*Wine* is an anachronism, install VirtualBox and you can run any version of Windows simultaneously with Linux (and CS5). For quick text on photos I use Sysinternal's ZoomIt.

---

### Post by amilypotter on 2012-02-16
Hie.. Very nice article.. Thanks for this great  information.. :)

---

