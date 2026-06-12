---
title: "Plugins and Codecs"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by nmartine on 2008-02-18
Running 7.10 on an old Dell Inspiron 1000 just did an install with Ubunutu only and now the codecs and adobe plugins won't download.  It says it can't find the codecs when I try and download them.  Any help is appreciated.


Nick

---

### Post by crjackson on 2008-02-18
> **nmartine said:**
> Running 7.10 on an old Dell Inspiron 1000 just did an install with Ubunutu only and now the codecs and adobe plugins won't download.  It says it can't find the codecs when I try and download them.  Any help is appreciated.


Nick

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by bodhi.zazen on 2008-02-18
A little off topic, but Linux Mint is based on Ubuntu and comes with the codics pre-installed.

---

### Post by nmartine on 2008-02-19
> **bodhi.zazen said:**
> A little off topic, but Linux Mint is based on Ubuntu and comes with the codics pre-installed.

I know, I've been meaning to put that on another machine to see how it is.  I've heard that it's too much like windows though.

Nick

---

