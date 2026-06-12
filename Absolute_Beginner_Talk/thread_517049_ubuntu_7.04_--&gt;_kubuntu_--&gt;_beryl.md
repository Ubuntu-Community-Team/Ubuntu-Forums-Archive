---
title: "ubuntu 7.04 --&gt; kubuntu --&gt; beryl ???"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by intransit on 2007-08-04
Hi all,

Firstly I have ubuntu fiesty 7.04 right. My basic understanding between kubuntu and ubuntu is KDE instead of GNOME interface. Rather than downloading kubuntu, 650mb or whatever, can I just install KDE or something with apt-get to make ubuntu kubuntu ?

Just so I can have a play with the different interfaces without having to do 2 seperate installs

And I understand I just have to download beryl with apt-get from ubuntu and I can use all those wicked visual effects. Will this also work in Kubuntu? I think some clarification is necessary hahah

---

### Post by bodhi.zazen on 2007-08-04
sudo apt-get install kubuntu-desktop

See the various guides for beryl/compiz ...

---

### Post by wolfen69 on 2007-08-04
```
sudo apt-get install kubuntu-desktop
``` when you log in, you will have a choice which one to boot into.

---

### Post by intransit on 2007-08-04
how big is that kubuntu-desktop going to be? > 100 mb?

So I just thought kubuntu would take over the ubuntu, but when you say it will let me choose, its installing another OS?

---

### Post by splintercellguy on 2007-08-04
No, it's simply installing another window manager and associated packages, the manager being KDE. Ubuntu/Kubuntu/Xubuntu are basically the same except different window managers and associated packages.

---

### Post by intransit on 2007-08-04
Thanks, that's what I thought.

"My basic understanding between kubuntu and ubuntu is KDE instead of GNOME interface. Rather than downloading kubuntu, 650mb or whatever, can I just install KDE or something with apt-get to make ubuntu kubuntu ?"

Nobody clarified. So in that case the file is likely not be very large at all. How do I figure out how big a package is before I download it? And why would it ask me which one I want to boot into - it should just set and if I want to change it I do it within settings in whichever environment

---

### Post by bodhi.zazen on 2007-08-04
Well, you can do a more minimal KDE installation with :

sudo apt-get install kde-core

The kubuntu-desktop is a "meta-package" so it installs KDE + the  default apps for Kubuntu + Kubuntu artwork.

Yes, you can modify user settings between gnome and KDE

You can run kde apps in gnome and gnome apps in kde ...

---

