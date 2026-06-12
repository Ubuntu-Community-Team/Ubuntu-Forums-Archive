---
title: "howto install gplflash?"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-25
hey I got the source and install build-essential and ran ./configure and got the error

configure: error: *** GPLFLash requires libz.

I can't find libz in synaptic. before this it asked for libjpeg and I found that. the dev version.

hmm... a deb would be nice...

or a suggestion for a different flash development gui?

thanx
sv

---

### Post by SOULRiDER on 2007-12-25
[http://packages.ubuntu.com/dapper/virtual/libz-dev](http://packages.ubuntu.com/dapper/virtual/libz-dev)

So try using zlib1g-dev
```
 sudo aptitude install zlib1g-dev
```

---

### Post by staticvoid on 2007-12-26
ok, I did that, now its saying 

configure: error: cannot find X11 development files

why can't it just list all of its dependencies all at once? and why is there no deb? :( boohoo..


sv

---

### Post by chewit on 2007-12-26
I wouldn't use gplflash. Its now stopped development. I use Pencil. Its still gets updates and support. Plus, its a .deb installer file.

[http://www.les-stooges.org/pascal/pencil/index.php?id=Home]("http://www.les-stooges.org/pascal/pencil/index.php?id=Home")

---

### Post by staticvoid on 2007-12-26
yeah, i have pencil....

i want to try gplflash or f4l

i'm pretty sure they are still in dev ?  :)

---

### Post by shareMenaPeace on 2007-12-26
Did you enabled all repos and software sources, from administration - > softeware sources, did you than updated?

I install flash witrh, i bworse to a flash site with firefox and than a message pops up asking me to install it...

---

### Post by staticvoid on 2007-12-26
no its not that I can't see flash in my browser, its that I want to design flash.

have you heard of pencil? it does 2d animation and can export to swf

i want to try all these free 2d programs to design nonfree flash

i thought gplflash is for development, and gnash is an opensource playerfor flash...

hmm... so how about more ideas to different 2d animating programs? I rendered this animation I did in blender then imported the pictures in pencil and had them all as frames then exported it as swf... cool, huh? like swift3d and flash, but free :)

sv

---

### Post by SOULRiDER on 2007-12-26
Itry installing libx11-dev [http://packages.ubuntu.com/gutsy/libdevel/libx11-dev](http://packages.ubuntu.com/gutsy/libdevel/libx11-dev)

```
sudo aptitude install libx11-dev
```

---

### Post by shareMenaPeace on 2007-12-26
cooool, thanx for the info staticvoid, im also into flash but used to macromedias .... 

cheers

---

### Post by staticvoid on 2007-12-26
yeah, me too...

but macromedia costs $ and i'm po
:(  

btw, shaweet video! [http://n00buntu.blogspot.com/2007/11/tutorial-ubuntu-compiz-virtualboxmagic.html](http://n00buntu.blogspot.com/2007/11/tutorial-ubuntu-compiz-virtualboxmagic.html)  :)

and niiice gallery

---

