---
title: "Ubuntu 10.4 + Midori + html5 youtube"
date: 2010-05-09
forum: Apple Hardware Users
---

### Post by New Horizon on 2010-05-09
I was playing around on my ibook g4 and thought I would try out Midori.  I was pleasantly surprised to see it would allow an html5 applet to open on youtube.  Sadly, the video never begins playing, so I believe I must need to install the non-free codecs package...if it does indeed contain h.264.

I've used Ubuntu off and on over the years, so my knowledge of how to do a lot things is quite limited.  I've been searching online for hours and can not find the information I need to install the non-free codecs...or just h.264 in general.

I saw one post about adding medibuntu repositories, but the address relating to nonfree codecs for the ppc gives a 404 when it is going through the apt-get update in the terminal.

Any assistance would be greatly appreciated.

---

### Post by linuxopjemac on 2010-05-10
I don't think it exists for ppc:
[http://www.mail-archive.com/medibuntu-maintainers@lists.launchpad.net/msg00511.html](http://www.mail-archive.com/medibuntu-maintainers@lists.launchpad.net/msg00511.html)
[https://launchpad.net/medibuntu/+announcement/3884](https://launchpad.net/medibuntu/+announcement/3884)

---

### Post by amsterdamharu on 2010-05-10
I can't get to youtube because it's blocked in China and I have mint installed anyway.

But the h.264 codecs are not missing from my system, they seem to be missing from firefox support of html5:
> 
Mozilla Firefox (3.5 and later) supports Theora video and Vorbis audio in an Ogg container.
Opera (10.5 and later) supports Theora video and Vorbis audio in an Ogg container.
Google Chrome (3.0 and later) supports Theora video and Vorbis audio in an Ogg container. It also supports H.264 video (all profiles) and AAC audio (all profiles) in an MP4 container.

I've tried some videos here:
[http://double.co.nz/video_test/](http://double.co.nz/video_test/)
And they all seem to work (but when I inspect the element with firebug they all point to an ogg file).

---

### Post by New Horizon on 2010-05-10
> **amsterdamharu said:**
> 
But the h.264 codecs are not missing from my system, they seem to be missing from firefox support of html5:


No, Firefox won't work with Youtube html5, but Midori will...if the codecs are supported under power pc that is.  Are you running power pc, or regular Ubuntu?  If it's power pc, how did you install the codecs?

---

### Post by New Horizon on 2010-05-10
> **linuxopjemac said:**
> I don't think it exists for ppc:
[http://www.mail-archive.com/medibuntu-maintainers@lists.launchpad.net/msg00511.html](http://www.mail-archive.com/medibuntu-maintainers@lists.launchpad.net/msg00511.html)
[https://launchpad.net/medibuntu/+announcement/3884](https://launchpad.net/medibuntu/+announcement/3884)

*sigh*  OH good, yet another roadblock. lol

Anyone know if I could build them myself somehow?

---

### Post by linuxopjemac on 2010-05-10
Where are the sources?

---

### Post by New Horizon on 2010-05-10
> **linuxopjemac said:**
> Where are the sources?

I'm not sure, but I'll see if they're out there.

---

### Post by linuxopjemac on 2010-05-12
There is still a jaunty ppc medibuntu repository:
[http://packages.medibuntu.org/jaunty/index.html](http://packages.medibuntu.org/jaunty/index.html)

x264 is the codec you need to see h.264 I think. I am new to this, I can't help further.

---

### Post by linuxopjemac on 2010-05-12
Interesting article by Mr Steve Jobs:
[http://www.apple.com/hotnews/thoughts-on-flash/](http://www.apple.com/hotnews/thoughts-on-flash/)

---

### Post by linuxopjemac on 2010-05-14
I tried a few things and I couldn't get it to work either. I am now working in Debian Squeeze and I added the multimedia repository. I have gstreamer0.10-x264, the 'good' and 'bad' gstreamer. I only see an HTML5 applet in youtube. No video...

---

### Post by oswaldkelso on 2010-05-14
To counter Mr Jobs :)

[http://weblogs.mozillazine.org/roc/archives/2010/01/video_freedom_a.html](http://weblogs.mozillazine.org/roc/archives/2010/01/video_freedom_a.html)

The reality is we all want unrestricted media like at [http://oggtv.com/](http://oggtv.com/) Apple can't offer us that any more than Adobe. Their little spat has nothing to do with anything but their business interests [http://news.bbc.co.uk/1/hi/technology/10113915.stm](http://news.bbc.co.uk/1/hi/technology/10113915.stm)

J. I also had the same issues as your self with Midori.

---

### Post by linuxopjemac on 2010-05-14
O: I stick to the mplayer trick you gave us a while ago. It plays youtube mp4/flv pretty nicely.

---

### Post by oswaldkelso on 2010-05-20
Midori + html5 youtube on my Debian testing box is working. Yes folks youtube working on PPC with out hacks.

---

### Post by linuxopjemac on 2010-05-20
Wow, good. I tried that but I couldn't get it to work. This is a breakthrough. What did you do to achieve this?

---

### Post by oswaldkelso on 2010-05-20
I just installed midori 0.2.4-3 went to the youtube html5 page enabled it and it worked. I didn't do anything special, someone else did :)

I'm on Debian testing 

Linux debian800 2.6.32-3-powerpc #1 Thu Feb 25 05:58:05 UTC 2010 ppc GNU/Linux

That's good. But what about google releasing VP8 

[http://forums.debian.net/viewtopic.php?f=3&t=52130](http://forums.debian.net/viewtopic.php?f=3&t=52130)

[http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/](http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/)

---

### Post by linuxopjemac on 2010-05-20
yes I saw that news about VP8...

---

### Post by KlavKalashj on 2010-05-23
h.264 works fine for me too on Midori. I don't think I did anything special, but I got ubuntu-restricted-extras installed, I guess that installed the x264 package, maybe that's what you need. I really hope vp8 support comes soon! Works fine in chromium, just copy-paste the code goddammit :D

---

### Post by linuxopjemac on 2010-06-19
I just did an upgrade in my test Squeeze partition on my loyal Pismo G3 and I also found out that html5 in Midori is working !!! No hacks indeed, just out of the box. My G3/400 is a bit too slow to play those videos in a good way. But those G4/G5 people might have better luck. This is excellent news for the PowerPC arch. Finally some 'normal' way to see Youtube videos.

---

### Post by oswaldkelso on 2010-06-19
Minitube is in Debian testing now (including PPC) so youtube is easy. No need for a browser even so great for old hardware.

---

### Post by linuxopjemac on 2010-06-20
Thanks for the tip Oswald...
I added to the bug report of Lightspark, asking to port it to PPC. If I have the time, I will try to do it myself in Squeeze. I tried it once in Lenny, but it was a nightmare.

---

### Post by linuxopjemac on 2010-06-20
It's extremely difficult to compile in PPC/Squeeze. I am not good enough to do this I'm afraid. I filed a request for adopting the package Lightspark in Debian. I will make a new thread in this forum whenever I have the confirmation. I hope many people will confirm this bug so there might be someone standing up to have the package in Debian.

Here is the package request:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=586529](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=586529)

---

