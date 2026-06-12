---
title: "Getting drivers"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-08-10
I've just instally Ubuntu on my laptop, and I assume that loads of things aren't working.  I can run a flashdrive through my USB, for example, but I don't think I can run a USB microphone.

And when I play DVDs the the screen is a mess.  Sure I'm probably missing some video drivers, but how on earth do I get hold of them?  

Obviously I can't expect anyone to solve my problems on this forum, but does anyone know any resources, to explain what's going on?  I mean, resources written in simple, accessible English, that don't zoom off into command lines without explaining what on earth they're talking about?

Not that I've got any problems with command lines - I enjoy using DOS -provided they're clearly explained - which in a Linux contenxt they're often not!  

So, any tips?  Because right now, having researched Linux, and tried it a bit on my laptop, I'm beginning to really appreciate the elegance and ease of use of Windows.

---

### Post by forestpixie on 2007-08-10
Hi - welcome make a start with Add/Remove in Applications ( I think) basically it's a store of apps, but its got codecs as well, you can select sound/video. also in the top right of that 'store' theres a show button click that to get more choice- have a look at the Multimedia sticky on the Abs Beg forum.

Later look at Synaptic in System >admin >synaptic - that's got all of the same and more 

And here is exactly the right place to come for help :D

---

### Post by amazingtaters on 2007-08-10
Ok, so for the DVD's you are going to need w32 codecs and libdvdcss2. Here's a good guide to getting those installed. [http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

As for the microphone someone else will have to help you

---

### Post by forestpixie on 2007-08-10
I'd go for the sticky to get those two packages - or the medibuntu pages

[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

I'm sure there's nothing wrong with your suggestion amazingtaters - other than the OP's going to have to get into editing sources list before he/she can start. 

But it's their choice :)

---

### Post by getmeoutofhere on 2007-08-10
Thanks for the tips - got Flash and Java working nicely.  DVD still a problem - it doesn't seem possible to edit the sources.list file, because it's read only.  There's doesn't to be anything to click on the text editor to allow it to be edited.

---

### Post by forestpixie on 2007-08-10
to edit the file you need root priveleges

open a terminal and enter 

gksudo gedit /etc/apt/sources.list 

and you'll be able to edit it, it might be an idea to back it up first

sudo cp /etc/apt/sources/list /etc/apt/sources.bak.1008

---

