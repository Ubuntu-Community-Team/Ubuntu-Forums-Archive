---
title: "Is Ubuntu for me? I need foobar2000 and web browsing"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by frtorreira on 2006-07-21
Hi all,

I am seriously considering migrating to Linux from XP. These are the main reasons:

1. I want to learn more about how OS work (learn how to tweak them etc.)
2. I want a bill-gates-free home

However, my computer should perform the following tasks:
 - play a reasonable number of audio codecs (ogg, flac, ape, all with or without cue sheets) gaplessly. This I can do in XP with foobar2000. It seems wine handles it pretty well. Has anyone tried foobar/wine under Ubuntu?

- surf the internet with a robust, good-looking browser. I installed Mandriva 2006 and was disappointed at the appearance of my favorite webpages, using either Mozilla or Konkeror. The fonts looked awful and badly aligned. Any way to make the browser look like firefox under windows? Listening to radio stations also proved unreliable when they  required Windows Media Player. Any way to get around this? 

So basically, if I were able to use foobar with most of its features (playback and conversion at least) and configure my web browser so that It looks somewhat better than the linux ones I have seen so far, I would definitely give Ubuntu a try.

I am ready to learn and spend time configuring my system. However, I would like to have some minimal warranty that eventually my computer will do these things just as my windows machine does (even after weeks of tuning). I would appreciate any kind comments.

Thanks in advance

---

### Post by Arisna on 2006-07-21
I've had better luck with a lot of things on Ubuntu than on other distributions, so it is likely that you would see better performance than on Mandriva.

As far as web browsing, Firefox on Ubuntu is great except for a couple of common problems.  There is no native Macromedia Shockwave support, and the workaround involves using a Windows compatibility layer and a another program to replace Shockwave objects in web pages with a Windows Shockwave objects.  Macromedia Flash for Linux is two versions old and does not work with some sites (you can trick some sites into thinking you have the latest versions and still use them), and a simple workaround is required to prevent Firefox from crashing when it encounters Vector Graphic content like Flash. Personally, I have neither Shockwave nor Flash on my installation, and I don't miss them much, but the case may be different for you.  I can't say I've had any problems with fonts or overall website display, though.

As far as music players are concerned, there are many options available on Ubuntu.  I do not know if any are as full-featured as Foobar 2000, though.  Conversion between different formats isn't something I've seen in any media player I've used, and on Ubuntu it's usually done via command line utilities like sox and lame, but you will certainly have playback.

---

### Post by T700 on 2006-07-21
Not sure about "foobar", but there are a wide variety of very nice audio and video apps for Linux.  My favorites are Amarok and XMMS (a WinAmp like program).  Check out my sig for the link to Automatix.  Automatix will install all the codec for you, along with lots of other things to make your experience more enjoyable.  It's easy and safe.

I use Firefox and just looking at it, can't tell if I'm in Windows or Ubuntu.  If that's not to your taste, try Opera 9.

Good luck and welcome to the forums!

Paul

---

### Post by GuitarHero on 2006-07-21
Ubuntu Firefox looks just like Windows Firefox.

---

### Post by qyot27 on 2006-07-21
With the fonts, there are two things:

1) Enable the multiverse repository and install the *msttcorefonts* package.

2) Copy the fonts from a Windows installation (in C:\Windows\Fonts) to a folder in /usr/share/fonts (I copied mine into /usr/share/fonts/windows, for instance).  There's better detailed instructions elsewhere on how to do this method correctly, as I seem to remember it requiring issuing a command to the system to index the fonts.  After said indexing, it should display more like what you're used to (not to mention having them available in programs like gedit and whatnot), although in my experience some things still don't look quite right, but it's still a substantial improvement.

---

### Post by steve.horsley on 2006-07-21
> **GuitarHero said:**
> Ubuntu Firefox looks just like Windows Firefox.

Except that the fonts are sooo much better! The fonts on Windows just look awful. All jaggy, no anti-aliasing at all.

---

### Post by frtorreira on 2006-07-21
Thanks for the info. This sounds like good news. There must have been something wrong with the browsers I saw on Mandriva. And it seems that Amarok playback capabilities are much like foobar's. I read a thread some time ago saying that it was not yet ready for foobar-like playback in terms of compatibilty, etc., but it seems things have changed :-) The only thing that bugs me now is how to play windows media player streaming files. I hear Real Player has a linux version. Since most radio stations I listen to brodacast either in real player or wmp formats, getting around wmp would be great!!

---

### Post by Jagot on 2006-07-21
> **frtorreira said:**
> The only thing that bugs me now is how to play windows media player streaming files. I hear Real Player has a linux version. Since most radio stations I listen to brodacast either in real player or wmp formats, getting around wmp would be great!!

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by PhrankDaChickenGeek on 2006-07-21
I personally like firefox in ubuntu better than XP. See for yourself. XP on the left, Ubuntu on the right.

---

### Post by frtorreira on 2006-07-21
Thanks for all the information. I will give it a try :-)

---

