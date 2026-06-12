---
title: "TV in &quot;Feisty&quot;"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by stoppage on 2008-02-13
Hi, I'm trying to bring in TV in „Feisty“ using Kaffeine and a Phillips-based saa7134 card. Card and driver are both recognised, I think the problem is that Kaffeine can't „bind“ properly. I'm new to this and I'd like to be clear on some points.....
because Kaffeine doesn't need a channels.config file, can I then deselect the „Enable dvb client“? If I do, then should I recieve TV using „Network Broadcasting....Recieve“ option? If I choose this I get a message saying „local host at port 8080....... no plugin found“. Any help greatly appreciated.
p.s. I have dvb-utils installed.

---

### Post by aBitLater on 2008-02-14
Hi stoppage,

I won't be much help here except to tell you that I had no luck with Kaffeine for my desktop ubuntu machine and a wintv pvr 150.  I ended up installing and setting up MythTV and got a guest subscription at schedulesdirect.org.

I could be way wrong here, but I think dvb device is for closed captions.

If you decide to install MythTV, it will take awhile - there a plenty of howto's on the net (search here and/or google) and there's a mailing list archive for any trouble you might want to search - try [www.mythtv.org](www.mythtv.org).  And, I can compare my specific setup with yours if that helps you to configure it.

---

### Post by stoppage on 2008-02-15
I eventually got my card to work with „TVTime“ but its way short of what I want. I'm looking for a solution similar to my TV software on Windows, iuVCR.....it's got record facility to various formats, DivX, XviD etc. I need something with its own scan. MythTV sounds really complicated, can I use the pre-compiled package and do I need to install Mplayer as well? And just one other question for the moment...do I need some sort of subscription for normal TV reception in Germany? If I don't find anything that looks a little less daunting then I'll try it although I don't know if it will function with this card.

p.s. for any interested parties, how I got my Phillips card working with „TVTime“...
added following line to  /etc/modprobe.d/options ...
„options saa7134 card=X tuner=Y" where X and Y respectively are the card and tuner numbers,which you will probably find in this wiki  [URL="http://gentoo-wiki.com/HARDWARE_saa7134#tuner"]http://gentoo-wiki.com/HARDWARE_
saa7134#tuner[/URL]

Later

---

