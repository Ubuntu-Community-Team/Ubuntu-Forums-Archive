---
title: "easy ubuntu 2.2 kiled my totem"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by thespinesplitter on 2005-10-05
[IMG]http://www.geocities.com/maxx_mcdick/totem-fuct.jpeg[/IMG] :mad:

---

### Post by darkmatter on 2005-10-05
thespinesplitter, could you provide more detail as to the root of your problem?

Did you log off/on again after you installed the additional components with easy ubuntu? This is some times require to complete the installation/configuration of some applications.

Also, are you running Hoary or Breezy? There are two different Easy Ubuntu's - 2.2 is for Hoary, and the 2.3 build is for Breezy.

More information regarding Easy Ubuntu may be found here:
[http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629)

If you could provide more details, it would better allow us to help you solve the problem.

---

### Post by thespinesplitter on 2005-10-05
the problem is i do not know the root of the problem, i have Hoary Hedgehog but i also used easyubuntu2.2 which is supposed to work, should i just upgrade and get breezy then use 2.3? it is the latest.
it wouldnt really be a problem since most of my data is on a windows partition, with easyubuntu i can get it running in 30 minutes with all i need

---

### Post by thespinesplitter on 2005-10-05
```
spine@dah-comp:~$ totem -v

(totem:10086): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(totem:10086): Gdk-WARNING **: locale not supported by C library
spine@dah-comp:~$
```

---

### Post by matthewv on 2005-10-05
if you run in terminal 
```

lsof /dev/dsp

``` you can see what other programs may be using the sound device
I think there is also another sound device besides /dev/dsp in /dev/sound that you might have to check. Once you know what probram is using the sound, just use
```

killall <program name>

```

You could also try going to System-->Preferences-->Multimedia Systems Selector and changing the default audio and video sinks to auto

---

### Post by thespinesplitter on 2005-10-05
for a while i had sound problems and it would start up even tho the sound devices were ocuppied, then if i tryied to play a file it would say-not possible alsa is beign used or sumthing, so i doubt thats the problem

---

### Post by thespinesplitter on 2005-10-05
it was the easyubbuntu alright


Failed to construct test pipeline for 'MJPEG (e.g. Zoran v4l device)'

Failed to construct test pipeline for 'XWindows (X11/XShm/Xv)'

the xwindows is all outta whack, im just giving up and upgrading to breezy and taking my chances again with easyubuntu

---

### Post by albertoramirez on 2005-10-05
I have exactly the same problem in Ubuntu, don't have any workaround???

---

### Post by thespinesplitter on 2005-10-06
im never going to fix this : (

---

