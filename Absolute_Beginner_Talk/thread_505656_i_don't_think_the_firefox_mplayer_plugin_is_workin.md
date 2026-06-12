---
title: "i don't think the firefox mplayer plugin is working"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-07-20
if i go to a site with an embedded video, the mplayer plug in just seems to be forever connecting and buffering .. and not actually playing anything.

i've seen the plugin that opens the video in a different window, but i s'pose in an ideal world, i'd want to try and get this one working if i can .. anyone have any ideas ??

---

### Post by kngunn on 2007-07-20
I saw this problem as well, but after loading the system with more audio/video codecs the problem went away.

Try grabbing the w32codecs.  You need to enable the universe/multiverse repos to do so.  (/etc/apt/sources.list).

You can also try "automatix" to load up on multimedia capabilities, but be warned that some folks have reported configuration troubles after running it.  I've used it without problem, though.

---

### Post by mgmiller on 2007-07-20
As long as you have mplayer installed, you should also install vlc.  Then try getting the media player connectivity extension for Firefox.  It will let you quickly switch between players.  I have found some sites like mplayer, some vlc and some totem.  It just seems to depend on the phase of the moon or some such silliness.

---

### Post by jasonwatkins on 2007-07-20
> **kngunn said:**
> I saw this problem as well, but after loading the system with more audio/video codecs the problem went away.

of course .. i'm a complete moron :)

one of the first things i always used to do on re-installing windows was grab the k-lite codec pack

arrrggghhh

thanks :)

---

### Post by jasonwatkins on 2007-07-20
well that didn't really solve the problem - i've installed quite a few codecs and went to a site to try it out and it did the same thing - just never got off connecting and buffering.

i pressed 'stop' on the player, and saw it was trying to buffer the whole video - even though i'd gone into the configuration and set it to only buffer 10% at a time, and set the cache size fairly small.

---

### Post by jasonwatkins on 2007-07-21
i'm still no closer to working this one out ..

i found [this test page]("http://www.public.iastate.edu/~rdalhoff/embedvideo.html") that plays all different type of embedded video.

the Real video embedded samples work fine, the Quicktime RTSP embedded video works fine - after you click 'start', but nothing else plays.

it just seems to permanently buffer and connect - i've installed lots of different codecs, so i'm just wondering if i still haven't installed enough ??

---

### Post by kngunn on 2007-07-21
Can you throw us a link to one of the problem locations.  I want to make sure I don't have the same problem with the site(s).  We can possibly compared some package lists then if need be to figure out what multimedia I've installed that you haven't.

---

### Post by jasonwatkins on 2007-07-22
> **kngunn said:**
> Can you throw us a link to one of the problem locations.  I want to make sure I don't have the same problem with the site(s).  We can possibly compared some package lists then if need be to figure out what multimedia I've installed that you haven't.

i'll try and find a link that isn't porn related then :D :D :D

---

### Post by pyros on 2007-07-22
It might also help to know what (relevant) packages you have installed.

---

### Post by jasonwatkins on 2007-07-22
i've just really nosed around for various codecs and installed them - i've installed a few of the gstreamer packages from the package manger as well.

---

### Post by pyros on 2007-07-22
> **jasonwatkins said:**
> i've just really nosed around for various codecs and installed them - i've installed a few of the gstreamer packages from the package manger as well.

if you just launch mplayer with the stream from the command line, does that work?

---

### Post by jasonwatkins on 2007-07-23
i've been doing some more digging and experimenting and I think it's really just one particular site - yourfilehost.com - which is causing me problems.

the plugin seems to be working well enough on other places, so i think i'll stick with things the way they are for now, and see how I go - cheers.

---

