---
title: "3rd party software"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by qureshia49 on 2007-10-24
Hi everyone,

I am also a newbie that finally decided to jump-ship from VISTA. I know there are many threads with a similar caption and maybe mine might be more specific. I am trying to install Adobe Photoshop, Macromedia Dreamweaver, Corel Draw, Camtasio Studio 4, Canvass X and some smaler programs. I don't know how to transfer them into the repository if that is required. I have working knowledge about the Synaptic & updating the repositories. But I am still unable to install 3rd party software. I downloaded these software in .bin and .rpm extension but I have no idea what to do with them.
Please would someone explain to me how and where to extract or how 3rd party softwares are dealt with.

I would appreciate it very much.

Thank you all.

Ash

---

### Post by Pumalite on 2007-10-24
Some Windows programs can be used with Wine: [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by stump138 on 2007-10-24
Just like Pumalite said, you should like at Wine for most of your windows apps.  If you are trying to install from .rpm, you need to convert it to .deb with alien

```
sudo apt-get install alien
```

usage:

```
 alien foo.rpm 
```

---

### Post by Hospadar on 2007-10-24
Getting your windows stuff running under linux is generally doable, but can be quite a protracted affair.
Wine will often run many programs just great, so that would be a good place to start.  If that doesn't work for you, the next route would be to run a virtual instance of windows with software like VMware.  There's a lot of documentation about this sort of thing on the web.

Many smaller applications you might have used in windows, especially open source ones, may well have a linux version, or a good linux alternative.  You should try browsing through Applications->Add/Remove.  Make sure you turn on "All available applications" in the upper right-hand corner of the window.

Few open source alternatives are to the same level of quality as their proprietary counterparts (adobe, etc) but many come close and are very good for most tasks.

---

