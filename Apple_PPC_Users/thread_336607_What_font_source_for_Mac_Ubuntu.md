---
title: "What font source for Mac Ubuntu?"
date: 2007-01-11
forum: Apple PPC Users
---

### Post by gurnemanz on 2007-01-11
The font handling of Ubuntu on Macintosh is perplexing me.

Are only TruType fonts supported (This would make my Type 1 font library obsolete)?

Something I saw in a post suggested either Mac or PC TT fonts would work on a Mac Ubuntu installation. Did I misunderstand?

- And a subsidiary question - what app is used for page layout work in Ubuntu?

Many thanks - the sharp edges of my ignorance now have a couple nicks in them.

g.

---

### Post by dpny on 2007-01-12
So long as you have the right modules loaded in your xorg.conf, Ubuntu can use Type 1 and Truetype fonts. Therer aren't really any differences between Mac and Windows Truetype fonts: Truetype is Truetype is Truetype, just as Postacript is Postscript is Postscript. The only Truetypish font Ubuntu can't read are Apple's system fonts, which use the .dfont extension. These are actually Truetype fonts with all of the non-OS X info stripped out, so that they can only be read by machines running OS X.

To add fonts to Ubuntu, create a folder in your home directory called ".fonts" and add the fonts there. [This](https://help.ubuntu.com/community/FontInstallHowto) is a good How To. I also followed [this](http://www.isolationism.com/2006-12-27/font-rendering-on-linux/) excellent link to much improve the font rendering on my Ubuntu install. I just copied the .fonts.conf file he includes in totality.

If you really want some of the OS X .dfonts on your machine, and have access to an OS X machine, there is a way. There is an X11 font editor for OS X called [FontForge](http://fontforge.sourceforge.net/) which will take any font and convert it to any other font. I have used it to turn Lucida Grande (one of OS X's .dfonts) and some other OS X fonts into notmal Truetype fonts and use them on my Ubuntu machine. They look great.

edit: I don't know about page layout software for Linux. That's what the G5 is for!

---

### Post by 3rdalbum on 2007-01-12
> **gurnemanz said:**
> 
- And a subsidiary question - what app is used for page layout work in Ubuntu?


Scribus is generally used for page layout. If typesetting is your profession, you're likely to be disappointed (I've heard Scribus described as "equal to QuarkXPress 3", which can't be good!). Otherwise, for casual stuff, it's great.

---

### Post by handylinux on 2007-01-12
Here's [a site]("http://unifont.org/index.html") dedicated to fonts in Linux/OSS which might be helpful.

> what app is used for page layout work in Ubuntu?
Haven't tried any yet, but [Scribus]("http://www.scribus.net/index.php") is the OSS answer to Quark/InDesign, and [Inkscape]("http://inkscape.org") to Illustrator. Both are still very much "in development", not yet ready for prime time, but they seem to be very much alive and growing -- and of course anyone can contribute, that's what community software is all about.

Another possibility, for small-scale page layout, might be OO, which has a draw module as well as word processing. Here's [a site]("http://openoffice.blogs.com/openoffice/2005/10/is_openofficeor.html") I came across that discusses using OO for page layout.

---

### Post by gurnemanz on 2007-01-12
Thank you! This has been very helpful!

g.

---

