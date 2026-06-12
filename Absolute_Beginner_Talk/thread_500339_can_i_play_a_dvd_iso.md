---
title: "can i play a dvd iso"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by xxchrisxx555 on 2007-07-13
i copied a dvd to iso and i want to know if i can play it in like mplayer or anything else

---

### Post by wink on 2007-07-13
Don't know about mplayer but it works for me using Totem.

---

### Post by FleetAdmiral74 on 2007-07-13
VLC has worked great for me in the past at playing ISOs. Its in the repos.

---

### Post by xxchrisxx555 on 2007-07-13
i get this error

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

i looked and i have libdvdcss2 installed

---

### Post by FleetAdmiral74 on 2007-07-13
Exactly how did you create the ISO?

---

### Post by 55Rebel on 2007-07-13
Go to: System > Administration > Synaptic Package Manager -  find 
 and Mark for Installation  *AcetoneISO2* and Apply--works great! 
After install you will find *AcetoneISO2* in Applications > Accessories.
I'm running Ubuntu 7.04 - Feisty Fawn.

Hope this helps.

Peace

P.S. 
Let us know if AcetoneISO2 works for your stated purpose, cuz i haven't actually used that app. for that purpose.
Acetone claims to be able to do that. thanks.

---

### Post by xxchrisxx555 on 2007-07-13
i tried that acetonel thing and it installed a bunch of kde things and didnt work

and to copy it i right clicked the disk in my desktop then copy

---

### Post by xxchrisxx555 on 2007-07-13
i got acidrip to work so i will just use that

---

### Post by RomeReactor on 2007-07-13
Hi. Check in Synaptic to see if you have **totem-gstreamer**; if you do, you may want to install **totem-xine** instead:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

---

### Post by JohnnyC44 on 2007-07-14
RomeReactor:  Having the same problem, I replaced Gstreamer with Totem-zine as you suggested.  Before I was getting the audio but no picture.  Now I get nothing.  Using plain vanilla Feisty here with no media tweaks.  Any suggestions?

---

### Post by RomeReactor on 2007-07-14
Hi **JohnnyC44**. Does this message show up?
> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

make sure you have all the necessary libraries:
```
sudo apt-get install libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
and then
```
sudo usr/share/doc/libdvdread3/install-css.sh
```
Also, you mentioned that with totem-gstreamer you had sound but no picture; your problem may be related to [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback").

Note that sometimes Beryl or Compiz (Desktop Effects) can interfere with video display; if either of those is installed and running, try disabling it and play the video.

---

### Post by 4Foot on 2007-07-18
> **55Rebel said:**
> Go to: System > Administration > Synaptic Package Manager -  find 
 and Mark for Installation  *AcetoneISO2* and Apply--works great! 
After install you will find *AcetoneISO2* in Applications > Accessories.
I'm running Ubuntu 7.04 - Feisty Fawn.

Hope this helps.

Peace

P.S. 
Let us know if AcetoneISO2 works for your stated purpose, cuz i haven't actually used that app. for that purpose.
Acetone claims to be able to do that. thanks.

55Rebel:

I read about this prog in Lifehacker and would like to try it. It does not appear to be in my repository however, I am running Feisty with Medibuntu as the only additional repositories. Any suggestions?

---

### Post by bulletxt on 2007-08-19
you can download their official deb.

I recommend you to download trevino deb from here. they are 2 files:

[http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0-1~3v1ubuntu1_i386.deb](http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/acetoneiso2_1.0-1~3v1ubuntu1_i386.deb)

[http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0~3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/feisty/3v1n0/fuseiso_20061017-0~3v1ubuntu0_i386.deb)


AcetoneISO2 does make iso play in players. of course if you don't have libdvdcss2 it's not AcetoneISO's fault..

---

### Post by asmoore82 on 2007-08-19
```
~ $ mplayer dvd:// -dvd-device *</path/to/dvd.udf.iso>*
```

---

