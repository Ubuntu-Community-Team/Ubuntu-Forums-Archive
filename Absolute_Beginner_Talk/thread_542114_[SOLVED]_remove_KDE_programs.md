---
title: "[SOLVED] remove KDE programs"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-09-03
I currently have all three of the most common WMs on my desktop, Gnome, KDE, and XFCE.  However, I've noticed that I get a lot of baggage along with the newly installed ones, notably KDE.  Many of these programs are redundant; for instance, I have Pidgin already, so why would I need Kopete?  So I tried going to the terminal and trying

```
sudo apt-get remove kopete
```

And it's fine with that except that it also wants to remove kubuntu-desktop, which I'm assuming means I would no longer have KDE.  Since the structure of Ubuntu is such that everything is freestanding (I believe when I started reading about it online before installing it somebody metaphorically referred to it as Legos) and can be added or removed, I would think it should be possible to pluck off these unnecessary programs, some of which - for instance Kaffeine - insist on being the default program when they don't work particularly well compared to those programs I have tweaked and added support for, such as MPlayer.  

On a semi-related topic, I have Rhythmbox in the menus in KDE but not in Gnome.  Does it not work in Gnome?  I haven't looked in Xubuntu yet.

---

### Post by vanden12 on 2007-09-03
Have you tryed removeing them from Add/Remove..

---

### Post by forestpixie on 2007-09-03
kubuntu-desktop, like ubuntu-desktop is a meta package (apparently ;) ) - basically if you remove part of the package - you haven't got the whole package anymore 

Don't worry - it's fine - I've apparently removed kubuntu-desktop and xubuntu-desktop when I was having a look at them both. 

The only thing to worry about is if you want to upgrade to the next version online you have to reinstall your system - that's not the whole thing just the bits you've removed 

as an example I installed the openoffice package instead of the ubuntu version - so I haven't actually got ubuntu-desktop - if I upgraded I would have to install ubuntu-desktop 
first, replacing my openoffice with the ubuntu one

Hope that makes sense to you - and if I'm wrong someone will say :)

---

### Post by univremonster on 2007-09-03
Huh, sure enough.  I removed Kopete and Kaffeine and a few others and KDE is still working fine.  I have a similar question which, if it doesn't receive attention here, I will post elsewhere, but here it is;

I have been using Rhythmbox as a music player for the last couple days and find that I prefer it to XMMS which I had been using before, but I can't figure out how to add it to my "Applications" dropdown, so I always have to open a terminal and type 'rhythmbox' and use it that way (though recently I added it to the panel, it really should go in applications->sound and video').  Any idea how to do this?

---

### Post by forestpixie on 2007-09-04
you could try right click on the mnin menu and then edit menu and add it in there - either by ticking the boxing or adding

---

### Post by univremonster on 2007-09-04
For a forest pixie, you sure know a lot of simple solutions to computer problems.  Thanks for the help!

By the way, since I read your signature, you are welcome to mark this as 'solved'

---

### Post by forestpixie on 2007-09-04
> you sure know a lot of simple solutions to computer problems


I don't know about that - I've certainly had a lot of problems with computers - everything I know about linux/Ubuntu I've managed to pick up in the last couple of months, I'm still new myself :) It's helped that the little one has been on summer hols - I've been able to read threads for the hell of it - and I have a handy little text doc that I paste things into

---

