---
title: "no music no startup sound"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-01-18
I saw a blurb about the startup and shutdown sound from ubuntu. Today I tried to play some mp3 stuff.  All this worked in windows so it isn't hardware. So far in ubuntu I havent heard a peep of anykind. 

Can someone please tell me where to look. War and peace is small compared to whats in here on sound and music.

---

### Post by zerhacke on 2007-01-18
Click SYSTEM - PREFERENCES - SOUND.

---

### Post by TheOtherLinuxFreak on 2007-01-18
> **mar225 said:**
> I saw a blurb about the startup and shutdown sound from ubuntu. Today I tried to play some mp3 stuff.  All this worked in windows so it isn't hardware. So far in ubuntu I havent heard a peep of anykind. 

Can someone please tell me where to look. War and peace is small compared to whats in here on sound and music.

same here. 'cept in Xubuntu. once i heard a sound but it was all fuzzy. so i need help too:-?

---

### Post by Tomosaur on 2007-01-18
MP3 files do not work by default on Ubuntu because the required codecs are not allowed (by law) to be shipped for free.

There are numerous solutions to these problems with multimedia. One is to download vlc:
```

sudo aptitude install vlc

```

Another is to download mplayer and the codecs packs from [here](http://www.mplayerhq.hu/design7/dload.html).

You may want to try a tool like [Automatix](http://www.getautomatix.com[/URL) which makes the installation of the required stuff very easy.


The fact that you hear no startup/shutdown sound could be an indicator of some hardware issues. Does sound work when you use the LiveCD?

---

### Post by TheOtherLinuxFreak on 2007-01-18
> The fact that you hear no startup/shutdown sound could be an indicator of some hardware issues. Does sound work when you use the LiveCD?

none for me.

---

### Post by mar225 on 2007-01-18
I went to system-pref-sound and went through the avaiable and there were several but the test is still silent.   I don't even get a startup sound when I boot up

---

### Post by carloslosgrande on 2007-01-18
Hi mar225, does your preferences box have the "play system sounds" ticked? and the Logout / Login options recorded as Logout and Login instead of "no sound"?
If so then you really need to set up the codecs.
As mentioned by Tomosaur you can use Automatix which will set these just fine.
Personally I use EasyUbuntu which you'll find here [HTML]http://easyubuntu.freecontrib.org/[/HTML]
for me this is the simplest and most effective as I'm simple but not effective.
Good luck.

---

### Post by Tomosaur on 2007-01-18
What is your soundcard (for those not hearing **any** sound)?

---

### Post by TheOtherLinuxFreak on 2007-01-18
C-Media PCI CMI8738 thats what it says in the sound settings. i had this same sound card in a diffrent pc and it worked

---

### Post by SubliminalKid on 2007-01-18
I have this same issue: no sound at all. I was using a soundblaster x-fi soundcard and it worked fine on windows. Linux does not seem to recognize that I have a soundcard seperate from my mobo(Intel ICH5)

---

### Post by TheOtherLinuxFreak on 2007-01-19
i was playing in the sound settings and i unchecked four speaker mode and it worked!

---

### Post by badtubist on 2007-01-19
what i do if go to system-preferences-sound and only get bug buddy?

---

