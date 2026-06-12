---
title: "WMV files not playing in Totem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by nssnskylinegtr34 on 2007-04-06
I tried to open a wmv file in Totem and it wouldn't play.  I've looked around and tried practically every common recommendation on how to fix it, and I still get the error message: > Totem could not play 'file:///home/joel/Desktop/patchesthehorse.wmv'. - You do not have a decoder installed to handle this file. You might need to install the necessary plugins.  Anyone know how to fix this?

Also, can anyone explain why programs like Totem didn't automatically come with the decoder?  It is a pretty common file type.

---

### Post by tbroderick on 2007-04-06
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Basically, it's a licensing issue.

---

### Post by sirhalos on 2007-04-06
A little known addon that most people never mention but I found very useful is the package gstreamer0.10-pitfdll this package allows you to use Windows DLL files for codecs which can be found on mplayers website. No need to use Mplayer.

---

### Post by tbroderick on 2007-04-06
> **sirhalos said:**
> No need to use Mplayer.

Except Totem isn't very good with DVDs.

---

### Post by Apollo17 on 2007-04-06
Hey there,

Go here for a good compilation of things to do to get Ubuntu up to speed on a lot of things that it can't come with due to licensing and patent restrictions:


[http://www.cs.cornell.edu/~djm/ubuntu/#hardware](http://www.cs.cornell.edu/~djm/ubuntu/#hardware)

Strange thing is that at Yahoo, sometimes the streaming videos work just fine, other times Totem-xine will not play them...but for the most part, I've got everything working just fine. Only thing left for me to install is Giam instant messenger and then I can't think of any other "have to have" items.

And I've only been using Ubuntu for two weeks now. Pretty amazing to think I put off learning about Unix and Linux for so long - boy was I dumb. In fact, other than iTunes and some CAD software, I could just about never fire up my XP PC.  (Wish there was a petition we could sign to Apple and AutoDesk asking them to port their programs over to Linux, but maybe virtualization will accomplish the same task one day).

One other suggestion to all the other newbies: take your time. Don't try to get everything working in the first couple hours after your install of Ubuntu. Ride the learning curve. And yes, I highly recommend buying "The Official Ubuntu Book" at Amazon. It is written in a easy, conversational style and had me up to speed on many aspects of Ubuntu quickly, or where to look on the  'net for more information. Worked for me!

Good luck,

Ross
Apollo17

---

### Post by nssnskylinegtr34 on 2007-04-07
Those don't help unfortunately.  I tried installing the various plugins but none of them worked, so I decided to install MPlayer.  When I tried to run ./configure it said I had the wrong version gcc, even though I have the correct one(s).  I also tried installing it through synaptic package manager but it said that necessary packages had "unresolvable dependencies"...any other ideas?

---

### Post by bobplano on 2007-04-07
automatix has quite a few codecs that you can install along with other useful programs. as for your gcc version, it may be 'too new' and it might not work with a few things. i dont know about synaptic though

---

### Post by Hutom on 2007-04-07
Automatix is not supported and often create serious problems. I installed it and then had to remove it. You can do without automatix. All necessary codecs (at least codecs that I found necessary for my porpose) are available from other sources. So better not go for automatix.

---

### Post by edvaldig on 2007-04-12
Totem sometimes makes me so pissed i wanna kill puppies :)

Anyway, why try to fix totem, get decoders installed etc, why not just get rid of totem from ubuntu and use mplayer for everything? Mplayer has never ever failed to do anything i've needed it to do, it plays EVERYTHING, if i'd ask it to play /dev/null it would display pretty colors just to make me happy :)

Edit: maybe i'll include some info on how to install mplayer:

make sure you have multiverse in your /etc/apt/sources.list
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse

> sudo apt-get update

just to make sure...
> apt-cache search mplayer 

> sudo apt-get install mplayer

> run in console: mplayer -fs anymediafileyouwant.avi or what ever (-fs is for fullscreen)

> and my personal favorite: mplayer -vo aa anymovieyouwant.avi (to get ASCII rendered movie :)) 

---

