---
title: "Playing music and video help"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by warpcrash on 2005-07-16
Ok when I try to play an mp3 in the default player on here it says some thing like needed plug in not found.  I have a nforce 2 mobo and the like startup sounds and stuff work on here.


what do i need to be able to play mp3s and video files and where do i get it and how do i install it.


also how the hell do i install these packages for linux when i wanna install a program.

---

### Post by DJ_Max on 2005-07-16
I could write a paragraph or two about mp3 codecs and using apt-get. But I'll just be repeating myself a thousand times. By showing you the guide. [http://ubuntuguide.org/](http://ubuntuguide.org/) I'm actually helping you a lot more, then holding your hand.

After that, if you have any questions, just post em.

Regards

---

### Post by Wolki on 2005-07-16
[QUOTE=warpcrash]Ok when I try to play an mp3 in the default player on here it says some thing like needed plug in not found.  I have a nforce 2 mobo and the like startup sounds and stuff work on here.


what do i need to be able to play mp3s and video files and where do i get it and how do i install it.


also how the hell do i install these packages for linux when i wanna install a program.[/QUOTE]

To install programs, use Synaptic. It's in your system settings menu, or you can start it with "sudo synaptic" on the command line.

In Synaptic you have to enable universe. Preferences -> Repositories -> Add and check universe.

To play mp3s with the default players Totem and Rhythmbox you need to install gstreamer0.8-mad. With Videos it depends on what kind of video you want to play. More info here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Usually, you don't install software you find in the internet, but get a version tailored for your Ubuntu. Use Synaptic for that. If you have Universe enabled as described, you should find most software you need.

---

