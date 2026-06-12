---
title: "DVD Player problems"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by thomp830 on 2006-07-26
I installed Ubuntu in my laptop yesterday (replacing SuSe). The problem is that I can't get DVDs to play. The computer does recognize the DVD but when I try to play it I get erro messages.
Any suggestions?
-Thanks
thomp830

---

### Post by arochester on 2006-07-26
Have you installed libdvdcss?

---

### Post by Perfect Storm on 2006-07-26
You might check: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ditdu on 2006-07-26
Where do you get libdvdcss from, and how do you install it?

---

### Post by Perfect Storm on 2006-07-26
If you read the link I gave you, you'll know: [https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by Skia_42 on 2006-07-26
Whenever I try to play a dvd I get an error message stating that the dvd cannot be played and then it asks me if I am trying to play it without dvdcss. I installed libdvdcss2 as discribed [here]("https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9") but it is still not working. Does someone know what I am missing?

---

### Post by Perfect Storm on 2006-07-26
Which player are you using?

---

### Post by ditdu on 2006-07-26
I'm using totem movie player. And when I tried to follow the instructions given, i was goven this message:

dpkg: status database area is locked by another process

The dvd still wont play, so i presume it didn't work!
Thanks for helping!

---

### Post by Perfect Storm on 2006-07-26
> dpkg: status database area is locked by another process

Means that something is running, like synaptic or apt-get. You have to close it/them first.

> I'm using totem movie player. And when I tried to follow the instructions given, i was goven this message:

Installed all the gstreamer stuff?

Also try mplayer and/or VLC (my favorite), they works much better (IMHO).

---

### Post by ditdu on 2006-07-26
I've installed all the gstreamer options, and the dvd plays.
However... it is skipping, and isn't in very good quality when i play it in full screen mode. 
(Sorry if I seem a pain, but I am a complete newcomer to all this :)   , so thanks for being patient!!!)

---

### Post by Perfect Storm on 2006-07-26
No problem we've all been newbie once :)


Do the same thing happens with other mediaplayers? If you havn't tried, you might give it a go.

---

### Post by ditdu on 2006-07-26
I tried Mplayer, and that came up with the following error message:

It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its xv support.
See 'mplayer -vo help' for other (non-xv) video out drivers. Try vo x11


I ran xvinfo in the terminal, and got the following:
X-Video Extension version 2.2
screen #0
 no adaptors present


I don't know what to do next, and know the video card is a 64Mb shared thing. (I don't know where to find out what it is!)

---

### Post by Skia_42 on 2006-07-26
Hey, I am still not able to play dvds. I installed libdvdcss2, all of the multimedia codecs, w32 codecs and the gstreamer files. Something else is eluding me but I don't know what it is. I have a PPC arctitecture but I do not think that would make a difference.

---

### Post by b1g4L on 2006-07-26
Try using EasyUbuntu to setup your DVD codecs - it should be fairly easy even for a beginner.

[http://easyubuntu.freecontrib.org/index.html](http://easyubuntu.freecontrib.org/index.html)

---

### Post by ditdu on 2006-07-26
(didn't know if you were aiming that at me!)
I've already used easyubuntu, as well as Automatix

---

### Post by avtolle on 2006-07-26
Skia_42: That might be an erroneous assumption. You might want to search the forum for threads dealing w/issues surrounding DVD playback and PPC arch.

---

### Post by b1g4L on 2006-07-26
> **ditdu said:**
> (didn't know if you were aiming that at me!)
I've already used easyubuntu, as well as Automatix

Does DVD playback work in Windows?

---

### Post by Skia_42 on 2006-07-26
According to easyubuntu, the codecs and dvdcss2 are already installed, I didn't find any PPC specific errors.

---

### Post by ditdu on 2006-07-26
> Does DVD playback work in Windows?

Yes, it works fine in windows, no skipping or anything... 
My ultimate goal though is to dispose of windows!  :D

---

### Post by Perfect Storm on 2006-07-27
> **Skia_42 said:**
> According to easyubuntu, the codecs and dvdcss2 are already installed, I didn't find any PPC specific errors.

Tried with diffrent players?

---

### Post by Skia_42 on 2006-07-27
> **Artificial Intelligence said:**
> Tried with diffrent players?

Thanks for posting, I was fearing this was a dead thread, I have tried totem, it loads the menu's but it cannot play actual chapters of the dvd. Gxine loads the menus but shows a black screen when I try to play the movie. Mplayer doesn't work, it returns and error message at startup, I tryed a reinstall to no avail. And I a not sure how to set-up VLC Player for DVD's.

---

### Post by Perfect Storm on 2006-07-27
It just seems strange that it can't see dvdcss2.

To change to make VLC starting when inserting a DVD:
[http://ubuntuforums.org/showthread.php?t=77146](http://ubuntuforums.org/showthread.php?t=77146)

---

### Post by Skia_42 on 2006-07-27
Okay, VLC recognized the disk, it showed the main menu of the dvd but when I tryed to play the actual movie the display screen closed leaving the control window. Sam problem as Totem or Mplayer.

---

### Post by Skia_42 on 2006-07-27
Okay, this is a list off alll the things I have installed concerning dvd playback: the multimeda and AUD-DVD Codecs from Automatix, libdvdcss2 and dvdread3 from Synaptic. Does anyone know what I am missing or a different method of installing the above?

---

