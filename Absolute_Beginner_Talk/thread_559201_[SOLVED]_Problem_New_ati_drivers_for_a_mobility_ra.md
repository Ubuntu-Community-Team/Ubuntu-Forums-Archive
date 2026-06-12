---
title: "[SOLVED] Problem: New ati drivers for a mobility radeon x1400"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-09-24
so, ATI released those nice, new drivers, and I installed the 32 bit package for my mobility radeon x1400 card with default settings. Now when I try to get xgl, my screen gets all mashed up, making everything barely discernible. -But it's there! I know I can just go back to the drivers provided in the repositories, but I'd really like to get the new ones up and running. Anyone got any experience with this?

Does the fact that the 32/64 bit versions of the driver both seem to link to the same file matter?

---

### Post by Fitzy_oz on 2007-09-24
> **OliverN said:**
> so, ATI released those nice, new drivers, and I installed the 32 bit package for my mobility radeon x1400 card with default settings. Now when I try to get xgl, my screen gets all mashed up, making everything barely discernible. -But it's there! I know I can just go back to the drivers provided in the repositories, but I'd really like to get the new ones up and running. Anyone got any experience with this?


I just had a look at the Linux ATi wiki and found this gem:
[B]This driver officially only supports the Radeon HD 2000 family. 
AMD recommends users of cards other than the ATI Radeon HD 2000 family continue to use the currently posted drivers for that product available for download on [http://ati.amd.com/](http://ati.amd.com/). Using the 8.41.7 driver with R500 series or earlier may be buggy. 

Future releases will return to a unified driver supporting all product families. 

The 8.41.7 driver has an entirely new codebase, and supports the new Radeon HD 2000 (R600) cards. More information at the Phoronix article below, and more to come. [/B]

It might be worth reverting to the older driver and waiting for the next release, A lot of people that I have spoken with have expressed the same sort of difficulties with OpenGL stemming from this release.  

At any rate here is the link to the ATi wiki, it's very handy: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by OliverN on 2007-09-25
> It might be worth reverting to the older driver and waiting for the next release, A lot of people that I have spoken with have expressed the same sort of difficulties with OpenGL stemming from this release.

ok, I probably will, then... Thanks for that link - very useful.
I once used [Greencastle's how-to]("http://ubuntuforums.org/showthread.php?t=488385&highlight=Xlib%3A+extension+XFree86-DRI+missing") to make an xgl session, and somehow this has gotten ruined. I can't even fix it by repeating it :( Any help there?

My screen now looks like [this]("http://www.flickr.com/photos/9439659@N07/1436448830/") when I log in to my beloved xgl session.

---

### Post by alienexplorers on 2007-09-25
Have you tried using the Envy script to load your drivers.

---

### Post by OliverN on 2007-09-25
> **alienexplorers said:**
> Have you tried using the Envy script to load your drivers.

No, but what a neat little app. The driver seemed to install correctly, but the result from booting into my xgl session is the same, though. Is there another way of 'activating' OpenGL? I'm thinking maybe all this updating has outdated my old, customized session?

Typing fglrxinfo in a terminal gives me

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6747 (8.40.4)
```

so I don't understand why I can't get OpenGL. Shouldn't it load in the default gnome session? Trying to load compiz I get

```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```

Please, anybody. I want OpenGL and compiz fusion back :)

---

### Post by OliverN on 2007-09-28
I'm gonna make a new thread with a different approach on this.

---

### Post by overdrank on 2007-09-28
> **OliverN said:**
> I'm gonna make a new thread with a different approach on this.

HI I don't think you need to make a new thread. The problem is you can search the forum and alot of user have problems with the ati cards. It has been my experience that when you install a graphics driver you need to completely  remove that driver and then install the new driver. So maybe back track and uninstall the new ati driver you install along with envy also. Then maybe you can try the restricted driver that is mentioned in the "how to" Good luck!

---

### Post by OliverN on 2007-09-30
> **overdrank said:**
> HI I don't think you need to make a new thread. The problem is you can search the forum and alot of user have problems with the ati cards. It has been my experience that when you install a graphics driver you need to completely  remove that driver and then install the new driver. So maybe back track and uninstall the new ati driver you install along with envy also. Then maybe you can try the restricted driver that is mentioned in the "how to" Good luck!

alright, I took care to uninstall current drivers, uninstall envy and reinstalling the previous ones, following the *exact* same procedure as I did originally. No luck.

---

### Post by OliverN on 2007-10-03
Solved. Ati drivers had messed up some fglrx packages that needed reinstall. Thanks for the help all the same.

---

