---
title: "A quick question about WINE 0.9.40"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-07-09
I just installed a program using wine 0.9.40 (Easy CD-DA extractor)  
Yes.. I want it.  (juicer is not enough for me)
So, the problem I'm having is... Once I open, the program  warms me that there is not any CD drive found.
Do I have to add a virtual drive in wine? I don't really know how wine works. I'm a newbe :)
Any idea?
Thank you mates.

---

### Post by Old Pink on 2007-07-09
What are you trying to do? Rip a CD? Tell us what you need, and chances are there's a native linux program out there that does it.

Otherwise, use the [**Wine Application Database**]("http://appdb.winehq.org/") to research the application you want to run, see how well it will run and what steps are needed to get it working. ;)

---

### Post by Anonii on 2007-07-09
> **Kosimo said:**
> I just installed a program using wine 0.9.40 (Easy CD-DA extractor)  
Yes.. I want it.  (juicer is not enough for me)
So, the problem I'm having is... Once I open, the program  warms me that there is not any CD drive found.
Do I have to add a virtual drive in wine? I don't really know how wine works. I'm a newbe :)
Any idea?
Thank you mates.
Open a terminal, and execute **winecfg**. A cute window will open. Get to the "drivers" tab.  A mere *Autodetect* does it for me, but if that is not the case for you, just create the CD-ROM drive yourself. For example, the path of my D: (CD-ROM drive) is /mnt/cdrom, and the Type is CD-ROM. 
Also, after applying your changes, open winecfg again and check if it's saved. I had an issue with that, and my settings would reset every time I closed winecfg.
If you need more help, the lads in #winehq ( @ irc.freenode.net) will be able to help you further.

Finally, from what I see, everything works fine with wine and the application you are trying to "emulate": [http://appdb.winehq.org/appview.php?iVersionId=7763](http://appdb.winehq.org/appview.php?iVersionId=7763)

---

### Post by Kosimo on 2007-07-09
> **Old Pink said:**
> What are you trying to do? Rip a CD? Tell us what you need, and chances are there's a native linux program out there that does it.

Otherwise, use the [**Wine Application Database**]("http://appdb.winehq.org/") to research the application you want to run, see how well it will run and what steps are needed to get it working. ;)


Hello. Thank you for your answer.

I want:
To rip a CD, and choose the bit rate, (128k 160k 192k...)  
the the encoding (mp3, ogg, wma, acc,..) 
An easy file conversor (ex: from ogg to mp3 choosing the bitrate and encoding) With destination folder
TAG EDITOR
Juicer... Doesn't allow me to do all this things with the same efficence than Easy CD-DA.
Otherwise I would use a native linux application for sure.

Any option? 
Thanks!

---

### Post by Kosimo on 2007-07-09
> **Anonii said:**
> Open a terminal, and execute **winecfg**. A cute window will open. Get to the "drivers" tab.  A mere *Autodetect* does it for me, but if that is not the case for you, just create the CD-ROM drive yourself. For example, the path of my D: (CD-ROM drive) is /mnt/cdrom, and the Type is CD-ROM. 
Also, after applying your changes, open winecfg again and check if it's saved. I had an issue with that, and my settings would reset every time I closed winecfg.
If you need more help, the lads in #winehq ( @ irc.freenode.net) will be able to help you further.

Finally, from what I see, everything works fine with wine and the application you are trying to "emulate": [http://appdb.winehq.org/appview.php?iVersionId=7763](http://appdb.winehq.org/appview.php?iVersionId=7763)

WOW!
This is exactly what I was looking for :) I can't try it tonight, but I'll try tomorrow ^^ :guitar:

Thanks again

---

