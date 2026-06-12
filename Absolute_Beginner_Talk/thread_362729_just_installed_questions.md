---
title: "just installed questions"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-15
I just got ubunto re-installed after a hard drive crash.  Can someone tell me, or point me in the direction of what packages are good to install first.  I know there are some programs that do everything for you, but I would like to know exactly what I am installing.  Things I definately need is something for MP3 playback, a pdf reader, and any extensions for Mozilla.  Anything else you can think of would be great.

Thanks

---

### Post by taurus on 2007-02-16
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by aysiu on 2007-02-16
First, enable extra repositories. This gives you more software to install at your fingertips.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then, understand the basics of installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Next, you can get MP3 playback:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

A PDF reader already comes with Ubuntu (it's called Evince; it's also known as Document Viewer). If, for some strange reason, you feel more comfortable with Adobe Reader, you can install that with this command: ```
sudo aptitude update && sudo aptitude install acroread
```

Extensions for Firefox can be found here:
[https://addons.mozilla.org/firefox/extensions/](https://addons.mozilla.org/firefox/extensions/)

Installing them is OS-independent (same for Windows, Ubuntu, Mac OS X). You go to Tools > Add-Ons > Extensions and Get Extensions. Find the extension you want and then Install Now. After you restart Firefox, the extension will be active.

---

### Post by rccharles on 2007-02-16
> **tim1970 said:**
> I just got ubunto re-installed after a hard drive crash.  Can someone tell me, or point me in the direction of what packages are good to install first.  I know there are some programs that do everything for you, but I would like to know exactly what I am installing.  Things I definately need is something for MP3 playback, a pdf reader, and any extensions for Mozilla.  Anything else you can think of would be great.

Thanks

You may want to look at EasyUbuntu.  See:

[https://wiki.ubuntu.com/EasyUbuntu](https://wiki.ubuntu.com/EasyUbuntu)

...

I do not know the difference between the referenced pages and EasyUbuntu.

Robert

---

### Post by koconnor100 on 2007-02-16
> **rccharles said:**
> You may want to look at EasyUbuntu.  See:

[https://wiki.ubuntu.com/EasyUbuntu](https://wiki.ubuntu.com/EasyUbuntu)

...

I do not know the difference between the referenced pages and EasyUbuntu.

Robert

easyUbuntu turns out to be a utility for downloading and installing a ton of packages that are most commonly wanted (playing copy protected commercial dvd's , mp3's , etc) all the things they should have included on the liveCD but forgot. 

I'm battering my head against a wall trying to get certain apps I want to use in Linux to work, they're almost here but not quite (example, the gcc compiler) but EasyUbuntu takes are of all that.

---

### Post by shareMenaPeace on 2007-02-16
> **koconnor100 said:**
> easyUbuntu turns out to be a utility for downloading and installing a ton of packages that are most commonly wanted (playing copy protected commercial dvd's , mp3's , etc) all the things they should have included on the liveCD but forgot. 

I'm battering my head against a wall trying to get certain apps I want to use in Linux to work, they're almost here but not quite (example, the gcc compiler) but EasyUbuntu takes are of all that.

For this i can also recommend

[http://getautomatix.com](http://getautomatix.com) an automatic installer which contains the most needed tools, utils, players codecs and such.

---

