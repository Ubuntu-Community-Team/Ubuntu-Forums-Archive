---
title: "Qdvdauthor"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Brian96 on 2007-07-07
I know this isn't a qdvdauthor forum, but I have a question or two.

First, after using 0.1.2 from the repos, I uninstalled it and compiled the program from the 1.0.0 tar.gz I downloaded from the website. That went fine.

However, when I click on Help => About in the program it shows version 0.1.5. How can this be if I compiled from the 1.0.0 tar?

Also, it crashes very, very frequently, including (but not limited to) every time I click on the properties of the mpeg file in the gui. Is this related to it being the "wrong" version?

Thanks

---

### Post by Brian96 on 2007-07-07
I found out that SOME of the crashing issues seem to be related to the fact that my CPU has Hypterthreading capabilities. After I disabled HT in the system BIOS I was able to get much more done with the software (though there were still random crashes).

Still not sure why the "About" dialog says 0.1.5.

---

### Post by ramjet_1953 on 2007-07-08
I know that this is off-topic, but I was having problems with this program, so I switched to [COLOR="Blue"]ManDVD[/COLOR], which runs very well on my hardware.

Here's a link:

[COLOR="Red"]http://linux.softpedia.com/get/Multimedia/Video/ManDVD-12812.shtml
[/COLOR]
Make sure that you also have these dependencies installed:

[COLOR="Blue"]Requirements:

· DVD Slideshow >= 0.7.5
· mencoder
· mplayer
· xine > 0.99.4
· lame >= 3.97
· dvdauthor >= 0.6.11
· mjpegtools >= 1.8.0
· netpbm >= 10.29
· transcode >= 1.0.2
· dvd+rw-tools >= 5.21.4[/COLOR]

Regards,
Roger :cool:

---

