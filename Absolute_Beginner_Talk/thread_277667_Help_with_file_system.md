---
title: "Help with file system"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-15
How would I go about seeing a list of all of the libraries and codec packs I've installed.

Where are they saved to.

Also, where are the programs I install through terminal saved to, like for example VLC.

is there a guide to understanding the file system of xubuntu/ubuntu?

thanks,
-c.

---

### Post by aysiu on 2006-10-15
```
dpkg -l
``` will list all the packages you have installed.

The installer files themselves are usually saved to /var/cache/apt/archives

The launcher files are usually installed to /usr/bin

If you use a package manager like Synaptic or Adept, you can usually filter or sort by what's installed.

As for the file structure, this is what I generally understand:
/boot - boot information, including Grub menu configuration
/etc - random default, system-wide preferences
/home - personal preferences and files
/lib - libraries
/usr - application launchers and other files (like documentation)

---

### Post by crimesaucer on 2006-10-15
thanks, 

I still am having a difficult time learning the file system.

any sites for beginners trying to learn xubuntu/ubuntu?

---

### Post by aysiu on 2006-10-15
I have a site with random tutorials:
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

When I first started out, I found this site helpful:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by crimesaucer on 2006-10-15
thanks, I love that wiki page, it's kind of why I need to check all of my installs because I went a bit crazy when I first found that list and installed all of my flash/java plugins and then installed the multi-media codecs in terminal from that page to go with my VLC and Xine, and then I found a tutorial about the Xine saying that all it needed to run good and play all files was:

ibxine-extracodecs and w32codecs.

and it also said that the w32codes come in two flavors, one from the mplayer page, and one from the debian package that is better because it was more file formats.

Would you know which one is the one that is included in the terminal code for multi-media codecs on the ubuntu wiki page?

I'm going to read the psychocatz tutorial, so thanks for the link.

---

### Post by CatKiller on 2006-10-15
> **crimesaucer said:**
> I still am having a difficult time learning the file system.

[Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

