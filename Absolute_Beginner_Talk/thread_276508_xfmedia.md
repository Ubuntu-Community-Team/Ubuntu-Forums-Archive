---
title: "xfmedia"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-13
GRRRRRR...
My mp3 files load into xfmedia but will not play on any program at all. I have xubuntu with all the trimmings as far as I know...

---

### Post by K.Mandla on 2006-10-13
I'm not 100 percent sure on this one (because I haven't tried it this way), but I think you want to install the [libxine-extracodecs]("http://packages.ubuntu.com/dapper/libs/libxine-extracodecs") package. 

To be honest, I've always preferred XMMS to xfmedia ... mostly because I was using Winamp way back at version 1.x, and it seems more natural to me. That being said, I have an easier time playing DVDs on xfmedia than mplayer or any other video player, so it does have some use. ;)

---

### Post by saintj0n on 2006-10-14
Interestingly enough, my mp3 works great on XMMS. Now if I could get flash sites to work on xubuntu...:confused: 

It seems to take a while to nail down all of the customization and configuration type of stuff on Linux. It would be cool if more people supported the Linux platform. Maybe then, it would be a little easier on the newbies...;)

---

### Post by JonahRowley on 2006-10-14
xfmedia uses the xine engine, so yes, you need to **apt-get install libxine-extracodecs**.  Flash you can install manually, but I find automatix works just fine and fixes most "problems" with Ubuntu.  Give automatix a try.

---

### Post by K.Mandla on 2006-10-14
> **saintj0n said:**
> Now if I could get flash sites to work on xubuntu...:confused: 
There is a Flash plugin; perhaps you've already tried it. 

[https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3](https://help.ubuntu.com/community/RestrictedFormats#head-c268ba69c6b38af1dc31ea09701c7d296cf971c3)

I usually just *sudo aptitude install flashplugin-nonfree*. It gets most of the Flash sites working, but as I understand it, we're still at Flash 7 and most everyone else is beyond that.

---

### Post by whoscheesemine on 2008-03-17
> **K.Mandla said:**
> I'm not 100 percent sure on this one (because I haven't tried it this way), but I think you want to install the [libxine-extracodecs]("http://packages.ubuntu.com/dapper/libs/libxine-extracodecs") package. 

To be honest, I've always preferred XMMS to xfmedia ... mostly because I was using Winamp way back at version 1.x, and it seems more natural to me. That being said, I have an easier time playing DVDs on xfmedia than mplayer or any other video player, so it does have some use. ;)

I am aware on how ancient this thread is, but the package will not install, does anyone know how to get xfmedia to play mp3's in the gutsy edition?

---

