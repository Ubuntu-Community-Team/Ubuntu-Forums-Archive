---
title: "w32codecs scrambled"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-07-11
Hi, 
 I'm running compiz and just installed a fresh version of ubuntu, but for some reason when i play a wmv file with kaffine its all scrambled, and when i play one with mplayer i get no video. every other format works fine. 

any help would be great thanks.

---

### Post by croak77 on 2006-07-11
Usually that means the wmv is DRM portected which cannot be played in linux. Have you tried different wmv's?

---

### Post by Compucore on 2006-07-11
Did you get the latest release through Automatix for the Codecs that you need. I know when I first tried I had a similar problem over here as well. After I had installed the codecs everything was fine afterwards.

Compucore

P.S. If you can't find it. Do a quick search for the add on program called Automatix here and do as the instructions says. And you'll be able to update a few things at the same time including the codecs.

---

### Post by jinxjinx on 2006-07-12
nope. i installed the latest codecs with automatix, but still scrambled. visualizations in totem are also scrambled. 

For some reason when i log in under meatcity and gnome they work. but when im using xgl and compiz they are scrambled...

---

### Post by croak77 on 2006-07-12
Did try changing the video driver for mplayer? If you open a terminal, type:
mplayer -vo gl2 file.wmv or if that doesn't work try it with -vo xv instead. You can also change the video driver in the mplayer gui under Preferences->Video Tab.

---

### Post by jinxjinx on 2006-07-12
thanks all better = )

---

### Post by Endow on 2006-07-12
I tried every driver on Prefernces->Video tab and none works.

(Oh ...:p  I have the excat same problem btw)

I dind't udnerstand those terminal inputs you provided...Am I supost to put the name of the file where you wrote file croak77 ??

---

### Post by croak77 on 2006-07-12
> **Endow said:**
> I tried every driver on Prefernces->Video tab and none works.

(Oh ...:p  I have the excat same problem btw)

I dind't udnerstand those terminal inputs you provided...Am I supost to put the name of the file where you wrote file croak77 ??

Yes file.wmv is your file you are trying to play. Are you using Compiz too? And does wmv work in Metacity?

---

### Post by Sonic Alpha on 2006-07-13
> **Endow said:**
> I tried every driver on Prefernces->Video tab and none works.

Have you installed the codecs/drivers via [EasyUbuntu]("http://easyubuntu.freecontrib.org/")?

---

### Post by Endow on 2006-07-13
croak77 : I used both commands and I got No video (due to missing codecs) in both of them.


Sonic Alpha : I have used Easy Ubuntu for other task more than once even (btw is that ok?to rerun the program again I mean) But I'm pretty positive there wer eno nvidia codecs in there.

---

### Post by croak77 on 2006-07-13
> **Endow said:**
> croak77 : I used both commands and I got No video (due to missing codecs) in both of them.


Sonic Alpha : I have used Easy Ubuntu for other task more than once even (btw is that ok?to rerun the program again I mean) But I'm pretty positive there wer eno nvidia codecs in there.

Did .wmv's work before you installed XGL/Compiz? Do you have the w32codecs package installed? 

```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```

---

