---
title: "Databending in Linux"
date: 2009-07-10
forum: Art &amp; Design
---

### Post by hellocatfood on 2009-07-10
I'm a recent convert to Ubuntu Linux from Windows XP. It's a great system but with it I've had to find equivalent software in which to do some glitching and databending.

btw, for those who don't know databending is a very raw method of editing files, in particular image and video files. Read [here for some more information](http://www.fizzpop.org.uk/blog/an-introduction-to-databending/)

Can anyone suggest any Linux sofware, particularly ones with a gui that are best used for glitching images, video and sound?

So far I've used mhwaveedit ([https://gna.org/projects/mhwaveedit](https://gna.org/projects/mhwaveedit)) as it allows the importing and saving of raw data and gimp ([www.gimp.org](www.gimp.org)) as you can save to quite a variety of formats (try .xpm for example).

Kate is good as it can open binary files but I still prefer to use gnome software (gedit doesn't open binary files)

Thanks for any suggestions!

---

### Post by tgalati4 on 2009-07-10
You can get creative in linux.

Try piping the mouse to the soundcard:

cat /dev/mouse > /dev/pcm

You'll have to do some searching to get the correct syntax.  Just don't mess with mem or kmem otherwise you will scramble the ram and lockup your system.

If you just want to mangle files:

apt-cache search hexedit
sudo apt-get install hexedit

hexedit munge_me_please.jpg

If you really want to see interesting, take an old ram stick and cut a trace, then try booting and using your system for a while.  Or better yet, try microwaving a ram stick.  Start out slow (say 30 seconds).  You want to induce just a little randomness, not kill it completely.

I don't know of any apps that do databending in real time.  Perhaps someone can whip up *MungeMaster* interactive photo enhancer/destroyer.

---

### Post by kayosiii on 2009-07-10
ghex is probably the animal you are looking for editing binary files.

Although not completely what you were asking -- you can do some cool stuff with video and effectv. [http://effectv.sourceforge.net/](http://effectv.sourceforge.net/)

---

### Post by hellocatfood on 2009-07-11
> **tgalati4 said:**
> You can get creative in linux.

Try piping the mouse to the soundcard:

cat /dev/mouse > /dev/pcm

You'll have to do some searching to get the correct syntax.  Just don't mess with mem or kmem otherwise you will scramble the ram and lockup your system.


Ah yes, I've heard of this before. Bit scared to do it though!

ghex is exactly what I needed!

Do you know of any other programs that will let you import raw data. I know that audacity and mhwaveedit will let you load any file but I wonder if there's a program that will try and interpret data as an image.

---

### Post by An85Zk9tc8rfjV8i on 2009-08-13
Lossy Compression of Jpeg with mp3 Compressors
Lossy Compression of mp3  with Jpeg Compressors

I saw a web site that did something similar once

quasi-random bit modification :
need to understand the file' data structure to avoid breaking it

digital to analog => "noisy" => analog to digital

---

### Post by hellocatfood on 2011-04-22
[Jean-Paul LeBreton](http://vectorpoem.com/) contacted me with information regarding glitches found when using hardware acceleration in mplayer (see attached files)

He's using Nvidia binary driver with geforce GT 240 card. Is anyone able to reproduce these results usingthe same card or with an ATI card?

---

