---
title: "kubuntu load screen after kubuntu-desktop uninstall"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by mdurkin on 2007-02-11
Hi All,
I just installed kubuntu-desktop on top of ubuntu to give it a go. Decided I prefer the normal gnome experience overall, so I uninstalled the package again. I did all this with aptitude.
Now I seem to be left with the kubuntu load screen instead of the ubuntu one. It's a small thing, but does anyone know how to get back to the default ubuntu load screen?!?
Thanks,
Matt

---

### Post by Ramses de Norre on 2007-02-11
```
sudo update-alternatives --config usplash-artwork.so
```
And choose the ubuntu one.

---

### Post by JustinAllen on 2007-02-11
Hiya! This is my first post...woot!  Hehe..anyway, I'm in the same boat you are.  I installed kubuntu-desktop last night through aptitiude and removed it as I prefer the gnome environment, but i'm left with the same splash screen.  Any help would be greatly appreciated :-)

---

### Post by JustinAllen on 2007-02-11
> **Ramses de Norre said:**
> ```
sudo update-alternatives --config usplash-artwork.so
```
And choose the ubuntu one.

I must've posted at the same time as you..hehe..anyway, i tried  your suggestion and it doesn't seem to work...this is what i get:

[B]There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
[/B]
Any ideas?

---

### Post by mdurkin on 2007-02-11
I get the same results!

---

