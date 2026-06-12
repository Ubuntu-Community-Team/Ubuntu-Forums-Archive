---
title: "playing video or dvds"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by stoneofshadow on 2008-04-12
sometimes my computer wont play videos or dvds 
i can hear the sound but the video is just a pink static
this happens on all programs and i restarting the computer fixes this
but is there any other way to fix it because that is a hassle

---

### Post by lsutiger on 2008-04-12
Have you installed the codecs? If not [follow this guide]("http://www.ubuntu1501.com/2007/11/easy-codec-install-for-gutsy.html").
The site is written specifically for the Dell Inspirion 1501, but that guide will work on any Gutsy 7.10 machine.

---

### Post by crjackson on 2008-04-12
> **stoneofshadow said:**
> sometimes my computer wont play videos or dvds 
i can hear the sound but the video is just a pink static
this happens on all programs and i restarting the computer fixes this
but is there any other way to fix it because that is a hassle

> **ravosava said:**
> I've read all of these "how tos" to make DVDs work, but for some reason, it wont. Can ANYONE help me? Any help is much appreciated. :)


Here, try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by carltondhouston on 2008-04-12
> **stoneofshadow said:**
> sometimes my computer wont play videos or dvds 
i can hear the sound but the video is just a pink static
this happens on all programs and i restarting the computer fixes this
but is there any other way to fix it because that is a hassle

So when you say it SOMETIMES won't play DVD's or videos, does that mean you can play home-made DVD videos, but not encrypted?  The way I read your question, it makes me think you can play DVD videos just fine, but video wigs out sometimes.

What else have you tried besides rebooting?  Does it continue if you go from full screen to windowed and vice versa?  What if you hit ctrl-alt-f1, then ctrl-alt-f7, which switches you between a text virtual console and back to the console X is running on.

Do you have desktop effects turned on?  Have you tried turning them off and seeing if the problem continues?

You say it happens in all programs, does that mean for DVD playback, or does other video output programs do the same thing, like flash video in your web browser?  Do you have any other video artifacts, like mouse tearing or any such other problems going on?  Is it JUST for video playback?

---

