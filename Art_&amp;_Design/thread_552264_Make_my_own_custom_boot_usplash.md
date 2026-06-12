---
title: "Make my own custom boot usplash?"
date: 2007-09-16
forum: Art &amp; Design
---

### Post by theunixgeek on 2007-09-16
Hi. I have some ideas for my own custom boot u splash. Nothing fancy. How can I implement it and have my own usplash? thanks.

---

### Post by matthew on 2007-09-16
This hasn't been edited in a while, so it is possible that it may be out of date. However, take a look at this wiki page and see if it gives you what you need to try doing this.

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

---

### Post by komputes on 2007-12-18
Can someone please update this information for Gutsy?

Thanks

---

### Post by smartboyathome on 2007-12-18
I would say use Splashy, it is way better than usplash imo and is easier to create themes for too.

---

### Post by komputes on 2007-12-20
Looks like people are having issues with it...

[http://ubuntuforums.org/showthread.php?t=41709&page=27](http://ubuntuforums.org/showthread.php?t=41709&page=27)

@smartboyathome: do you have a link for a good splashy tutorial? Do you know of any themes that go further than displaying just a standard horizontal progress  bar?

---

### Post by smartboyathome on 2007-12-20
> **komputes said:**
> Looks like people are having issues with it...

[http://ubuntuforums.org/showthread.php?t=41709&page=27](http://ubuntuforums.org/showthread.php?t=41709&page=27)

@smartboyathome: do you have a link for a good splashy tutorial? Do you know of any themes that go further than displaying just a standard horizontal progress  bar?

Try following the Ubuntu installation guide on [this page]("http://splashy.alioth.debian.org/wiki/ubuntu") to install it on Ubuntu, do exactly what it says and you shouldn't have much trouble. Remember to update your initramfs each time you change your theme by running this command:

```
update-initramfs -u -t -k `uname -r`
```

Here are the [official theme docs]("http://splashy.alioth.debian.org/wiki/themes") which I found useful for creating splashy themes. It can be frustrating getting the themes right on the command line, but they are comming out with a GUI soon for creating themes. [Here]("http://www.gnome-look.org/content/show.php/SplashyCreator?content=67618") is a third party GUI if you want it.

All splashy themes show the output over the theme by pressing F2 (I find this better than pressing ctrl+alt+F1 using usplash).

---

### Post by komputes on 2008-01-07
So will splashy allow me to export usplash compatible files (that can replace the current usplash) or is it another system completely, because I am only interested in making usplash compatible boot splash screens. I have tried time and again with the tutorial on the documentation website with no success. Anyone able to write a  good guide on creating a custom usplash on gutsy wins one free internet!!!

---

### Post by smartboyathome on 2008-01-07
It is a completely different system.

---

### Post by komputes on 2008-01-17
I'm still looking for a solution to create a usplash on Gutsy. Has anyone ever made a custom usplash on gutsy?

---

### Post by shababhsiddique on 2009-11-29
I know it is too late. Still may be this could help someone in future-

[http://lunatic.no/usplash/](http://lunatic.no/usplash/)

A usplash maker

---

### Post by Dr Belka on 2009-11-29
I hate usplash, or at least, making custom usplashes.  I can only get it to work if I only edit the background image, not the throbber.  When I do get that to work, the colors on the throbber are really messed up.  When I do edit the throbbers, the things wont even work at all.  Very frustrating.  I know I am missing something, I just can't figure out what!!!

This is the guide I found to be fairly informative.  [http://www.flyninja.net/?p=884](http://www.flyninja.net/?p=884)

---

