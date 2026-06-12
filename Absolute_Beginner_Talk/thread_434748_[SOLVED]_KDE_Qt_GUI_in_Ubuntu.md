---
title: "[SOLVED] KDE Qt GUI in Ubuntu"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by gmjs on 2007-05-06
Hi,

This is a bit of a silly question really, but I've installed a few programs that use Qt under Ubuntu with the Gnome Desktop Environment (e.g. Scribus, LyX).  They work, but the interface does not look as good as it does under KDE.

Is there are particular package that I can install to get the slightly better GUI in these applications?  I did find a Qt Configure dialogue which let you choose a look for Qt, but it has not made a difference.

I have managed this before in a previous installation of Ubuntu, but I think I had to install the whole of the KDE, which I would prefer not to do (I like the Ubuntu splash screen too much - pathetic hey)!

Many thanks,

Graham

---

### Post by machoo02 on 2007-05-06
I think what you are looking for are just the core KDE libraries:```
sudo aptitude install  kdelibs4c2a 
```might do the trick

---

### Post by gmjs on 2007-05-11
Hi,

Yes - it was exactly that!  Thank you so much.

Sorry for the late reply (been without a PC for a few days :( )

Many thanks,

Graham

---

