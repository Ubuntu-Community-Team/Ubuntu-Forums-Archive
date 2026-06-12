---
title: "Arch Linux package management during installation?"
date: 2013-01-22
forum: Any Other OS
---

### Post by oscarivera9 on 2013-01-22
Has anyone come across a good, easy to follow manual for how to install Arch Linux?
Ubuntu is my favorite distro and I'm currently using Ubuntu 12.04.1LTS, however I also like to try other systems as well.  Recently I figured I'd try installing Arch through Virtual Box before commiting to installing on a real physical drive.
  The lack of a graphical installer sure makes things a lot tougher than I expected.  I had read in multiple places that the Arch Wiki provided good detailed instructions for the installation, and it does.  However, when I finally hit a roadblock was when I got to the package management section.  I have an idea of what I want installed but it was in choosing the correct dependencies and such that I felt somewhat lost.  If anyone has any suggestions, I would love to hear what you've got to say about package management to make an easy installation of Arch Linux.

---

### Post by smellyman on 2013-01-22
You made it through the hard bits.  It's actually the easy part now.  Do just what they say.  install X and install input and video drivers....fonts.  Pacman will take care of the dependencies for you

If the testing of X is successful then just jump to install your DE/WM of choice gnome, kde, openbox etc....

You could watch a man in drag do a demo for you. :)

[LINK]("http://www.youtube.com/watch?v=VJb6bZm5QOc") to the youtube vid

---

### Post by Cheesemill on 2013-01-22
Just follow the [Beginners Guide]("https://wiki.archlinux.org/index.php/Beginners%27_Guide"), it takes you through getting your system installed. Then just follow the instructions on the relevant wiki page to install your DE of choice.

There is no need to worry about dependencies, pacman will take care of that for you.

There really isn't any advice that we can give you that isn't already covered in the wiki, it's one of the best Linux resources around.

---

### Post by oscarivera9 on 2013-01-22
> **smellyman said:**
> You made it through the hard bits.  It's actually the easy part now.  Do just what they say.  install X and install input and video drivers....fonts.  Pacman will take care of the dependencies for you

If the testing of X is successful then just jump to install your DE/WM of choice gnome, kde, openbox etc....

You could watch a man in drag do a demo for you. :)

[LINK]("http://www.youtube.com/watch?v=VJb6bZm5QOc") to the youtube vid

Thanks for the video and the advice.  I didn't know Pacman would take care of the dependencies. I feel much better about it now.

---

### Post by oscarivera9 on 2013-01-22
> **Cheesemill said:**
> Just follow the [Beginners Guide]("https://wiki.archlinux.org/index.php/Beginners%27_Guide"), it takes you through getting your system installed. Then just follow the instructions on the relevant wiki page to install your DE of choice.

There is no need to worry about dependencies, pacman will take care of that for you.

There really isn't any advice that we can give you that isn't already covered in the wiki, it's one of the best Linux resources around.

So you're the second person to tell me not to worry about the dependencies, that's definitely comforting.  As far as DE, I like Xfce but I wouldn't mind sticking with KDE; after all, it seems like Arch is more of a KDE oriented distro and thus it may feel and work better under KDE.  What do you think?

---

### Post by bfmetcalf on 2013-01-22
Arch is not oriented to any DE in particular.  In fact if you look at some of the threads on the arch forums you will find most people are just running an window manager like DWM or Openbox.  I say install what you want, in the case of XFCE it would be ```
pacman -S xorg-server xorg-xinit xorg-server-utils xfce4
```

The WIKI is amazing for installing pretty much anything, here is the XFCE Page..... [https://wiki.archlinux.org/index.php/Xfce#Installation](https://wiki.archlinux.org/index.php/Xfce#Installation)

and make sure to run a ```
pacman -Syu
``` often to keep everything up to date.

---

### Post by oscarivera9 on 2013-01-22
> **bfmetcalf said:**
> Arch is not oriented to any DE in particular.  In fact if you look at some of the threads on the arch forums you will find most people are just running an window manager like DWM or Openbox.  I say install what you want, in the case of XFCE it would be ```
pacman -S xorg-server xorg-xinit xorg-server-utils xfce4
```The WIKI is amazing for installing pretty much anything, here is the XFCE Page..... [https://wiki.archlinux.org/index.php/Xfce#Installation](https://wiki.archlinux.org/index.php/Xfce#Installation)

and make sure to run a ```
pacman -Syu
``` often to keep everything up to date.

Way cool!  Thanks for the info.

---

### Post by Cheesemill on 2013-01-22
What makes you think that Arch is KDE oriented?

One of the key features of Arch is that it uses unpatched source code directly from upstream (unlike Ubuntu which heavily patches a lot of applications to fit in with the Ubuntu way of doing things).

When you install any DE on Arch it is being used as the original developers intended, there is no one DE that is optimized for Arch.

Personally I have used KDE, Openbox, XFCE and Gnome on my Arch installations. They have all worked flawlessly.

This is what my Arch workstation running Gnome looks like at the moment...

[[IMG]http://ompldr.org/taDZuaA[/IMG]]("http://ompldr.org/vaDZuaA")   [[IMG]http://ompldr.org/taDZuag[/IMG]]("http://ompldr.org/vaDZuag")

Everything you could possibly want to know is on the wiki...
[https://wiki.archlinux.org/index.php/DE](https://wiki.archlinux.org/index.php/DE)

---

### Post by bfmetcalf on 2013-01-22
for reference, this is my Arch install running openbox...

[[img]http://ompldr.org/tZ3hpbA[/img]](http://ompldr.org/vZ3hpbA)

[[img]http://ompldr.org/tZ3hqMQ[/img]](http://ompldr.org/vZ3hqMQ)

---

### Post by oscarivera9 on 2013-01-29
I got a lot of good responses from many of you.  This is why I love Ubuntu,  because the Ubuntu community is awesome!
I want to thank everyone who contributed in educating me about Arch, your help has been very valuable.

---

