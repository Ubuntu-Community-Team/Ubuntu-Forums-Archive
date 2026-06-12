---
title: "Ubuntu 10.04 LTS - no sound on G4 powerbook"
date: 2011-12-19
forum: Apple Hardware Users
---

### Post by john amino on 2011-12-19
hello

as the thread title says....installed 10.04 on my g4. all lovely, except for having no sound....hich is annoying, as i'm a musician!

super new to ubuntu and linux, so please be gentle. But any help on getting this fixed would be greatly appreciated

thanks

john

---

### Post by rsavage on 2011-12-19
Hi John, sometimes you don't get sound because a channel has muted itself.  This sometimes happens if you've tried to suspend?  You probably have some nice graphical mixer, but if you goto a terminal and type the command:

```
alsamixer
```you will get a very basic one.  Turn up the channels and see if that solves it?

EDIT: just to say the letter m toggles mute in alsamixer

---

### Post by john amino on 2011-12-19
hmmm...that doesn't seem to be the problem. 

any more ideas? :D

---

### Post by john amino on 2011-12-19
wait. no. it did fix it!!

many thanks 

all good

---

### Post by rsavage on 2011-12-19
Excellent! It's always best to look for the easy answer first! There are more hints and tips here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) . Although it is based on lubuntu, most of the stuff is applicable to normal Ubuntu too. Have you had a look into Ubuntu studio? This is their audio meta package [http://packages.ubuntu.com/lucid/ubuntustudio-audio](http://packages.ubuntu.com/lucid/ubuntustudio-audio) .  See also [https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList) .

---

