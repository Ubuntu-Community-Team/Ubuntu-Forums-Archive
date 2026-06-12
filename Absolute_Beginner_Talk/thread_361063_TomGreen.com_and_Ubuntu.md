---
title: "TomGreen.com and Ubuntu"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by myodometer on 2007-02-13
I've only recently attempted to set my computer up to dual-boot XP and Ubuntu.  I like Ubuntu so much, though, that I'm using it much more often than I am Windows.  Unfortunately, one of my favorite things on the internet is the new Tom Green Show at tomgreen.com and it just doesn't want to play nicely with my Firefox or my Totem program.

I've done some extensive searching for an answer to my problem and followed all of the steps provided here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
All that this did for me was to allow me to stream the audio from the show, but I'm not getting any video.  The audio only seems to want to stream through Totem - the MPlayer extension that I tried to install on my Firefox hasn't shown any signs of life since I installed it.

Any ideas?

---

### Post by confused57 on 2007-02-13
> **myodometer said:**
> I've only recently attempted to set my computer up to dual-boot XP and Ubuntu.  I like Ubuntu so much, though, that I'm using it much more often than I am Windows.  Unfortunately, one of my favorite things on the internet is the new Tom Green Show at tomgreen.com and it just doesn't want to play nicely with my Firefox or my Totem program.

I've done some extensive searching for an answer to my problem and followed all of the steps provided here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
All that this did for me was to allow me to stream the audio from the show, but I'm not getting any video.  The audio only seems to want to stream through Totem - the MPlayer extension that I tried to install on my Firefox hasn't shown any signs of life since I installed it.

Any ideas?

You might want to look into automatix2:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Automatix2 will install codecs, mediaplayers, flashplayer,etc...automatically.

---

### Post by seshomaru samma on 2007-02-14
I would personaly only use automatix as a last resort
if automatic messes up your system ,it can't be fixed

from the ubuntu community page:
> Warning Regarding Alternative Installation Methods

Warning: [WWW] EasyUbuntu and [WWW] Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release.


try to install gxine and totem first
BTW- i just tried tomgreen.com at work on a Windows computer and the videos didnt work on both Firefox and IE

---

### Post by DerArzt on 2007-02-14
If i were you i would install easyubuntu. it grabs all the codecs for playing embedded video. It will also install things such as java and flash. in general, it is very useful. It can be found through Synaptic Package Manager.

---

### Post by fenian on 2007-02-14
Install [flash]("https://wiki.ubuntu.com/FlashPlayer9?highlight=%28flash%29") plugin.
Then install mplayer and plugin with this command...

> sudo apt-get install mplayer mozilla-mplayer

---

### Post by myodometer on 2007-02-17
Well, I ended up trying out EasyUbuntu and that seems to have done the trick.  I can't view the feed embedded in the page, but I can get it to work in Totem when I've got it as a standalone.  Ideally, I'd like to fix this in the future - but this should be enough to satiate my TG addition for the time being.

Thanks for the help!

---

