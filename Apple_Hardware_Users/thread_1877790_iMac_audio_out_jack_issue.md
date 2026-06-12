---
title: "iMac audio out jack issue"
date: 2011-11-08
forum: Apple Hardware Users
---

### Post by Proinsias on 2011-11-08
I recently got a new iMac. It's dualbooting ubuntu 11.10 and Lion nicely.

Everything is hunky dory aside from the audio out jack. The iMac speakers are awful. I've got it plugged into a little Technics system to give it some oomph, which works fine with lion. In ubuntu the audio comes out the internal speakers only. It seems to be oblivious to the audio out jack.

Any ideas?

Happy to post any info required but really not sure what is relevant. I've done a little digging around and after a few weeks feel like I'm getting nowhere.

Thanks

I'll try to post any info required but I'm not overly skilled in the ways of the terminal.

---

### Post by ptitdoon on 2011-11-09
Hi,
I am facing exactly the same problem...
I managed to get a good sound quality from the screen speakers using the 2 models:
422	  mbp55		MacBook Pro 5,5
423	  imac27	IMac 27 Inch
in /etc/modprobe.d/alsa-base.conf
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)

This is working since I re-installed the fglrx driver for the graphic card. Using non-proprietary driver led to no sound.

BUT...when I plug headphones in the jack, nothing changes and sound still comes from the screen.

And I also have an awful watermark on my screen (AMD unsupported hardware)...

Don't know if that helps a little...sorry for my english and my poor knowledge, that's my 2 cents!

---

