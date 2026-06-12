---
title: "Installing Automatix on a Gusty setup"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Vega on 2007-12-26
I never got this before but after installing Gusty

I can't seem to get automatix installed in .deb package and even through terminal

> E: Package automatix has no installation candidate
virtue@virtue-laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automatix is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  automatix2
E: Package automatix has no installation candidate
virtue@virtue-laptop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automatix is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  automatix2
E: Package automatix has no installation candidate
virtue@virtue-laptop:~$ 


---

### Post by ubername on 2007-12-26
Why do you want automatix? I have upgraded from various previous versions of ubuntu to Gutsy and have no need for automatix (I don't think it is well liked for various reasons.)EDIT: I used automatix before (for nVidia drivers IIRC), but don't need it in Gutsy

---

### Post by asmiller-ke6seh on 2007-12-26
It's getting to be that Automatix is becoming less and less necessary to use in Ubuntu. What are you trying to do with Automatix - there may be a safer and more reliable way to do it - things like installing the non-free codecs and such - and it may even be easier (or just as easy) without Automatix.

So, what are you trying to accomplish with Automatix - we can probably guide you how to accomplish that without Automatix.

   :guitar:

---

### Post by overdrank on 2007-12-26
You may have a look here
[http://ubuntuforums.org/showthread.php?t=396306&highlight=automatix&page=5](http://ubuntuforums.org/showthread.php?t=396306&highlight=automatix&page=5)
And what are you trying to install and maybe we can help.

---

### Post by Vega on 2007-12-26
all codecs(DIvX, XviD, MP4, OGM, MKV) including those on w32

flash, an optimized version of Firefox, 

Stream WMV, etc..

---

### Post by overdrank on 2007-12-26
> **Vega said:**
> all codecs(DIvX, XviD, MP4, OGM, MKV) including those on w32

flash, an optimized version of Firefox, 

Stream WMV, etc..
Hi and these links will help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by Vega on 2007-12-26
^  I tried one of your methods and I made a little bit of progress on youtube, but it brings up a dialog for a suitable codec, I try and download it but this is what I get
> Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

---

### Post by overdrank on 2007-12-26
> **Vega said:**
> ^  I tried one of your methods and I made a little bit of progress on youtube, but it brings up a dialog for a suitable codec, I try and download it but this is what I get

Ok then you can go to synaptic manager and search for gestreamer ugly and install.

---

### Post by ajgreeny on 2007-12-26
I would suggest you remove totem-gstreamer and install totem-xine instead.  It is so much better in my opinion, certainly so for dvd playback, but also in most other ways.

---

### Post by bodhi.zazen on 2007-12-26
> **Vega said:**
> I never got this before but after installing Gusty

I can't seem to get automatix installed in .deb package and even through terminal

Automatix is not supported on the Ubuntu forums.

If you would like help with automatix, please post on the Automaitix forums.

Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

If you have a specific question, please start a new thread.

---

