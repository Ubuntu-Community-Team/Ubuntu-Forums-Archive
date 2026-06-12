---
title: "Linux developer assistance - CD Autoplay"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by dmorison on 2008-02-29
Hi, I am new to Linux, despite Ubuntu being my second successful installation - I didn't really get anywhere with my first (SUSE).

I've only developed in a Windows environment before, but I want to start a small project and am after guidelines of where to start.

I would like to create software that will autorun when an audio cd is detected, and will give the user the choice of ripping the audio to disk (and where to save it), or playing from the cd.  These operations will almost certainly invoke other applications.

So I am envisaging a script to handle the audio cd detection and autorun functionality, and a graphical application to let the user select where to save the music or to play from a CD.  This will in turn run a shell command to carry out either operation.

Any help on this is appreciated - any code samples or suggested technologies..

Obviously if someone knows of software that will already do this I am interested in having a look.

Thanks,

Dave

---

### Post by Crooksey on 2008-02-29
HAL is software that deals with automounting media, and then Gnome can usually tell what type of media is in on the media, then handle it accordingly.

---

### Post by dmorison on 2008-02-29
Thanks for the response - I'll check it out.

---

