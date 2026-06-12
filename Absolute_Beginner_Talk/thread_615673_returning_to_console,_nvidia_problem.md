---
title: "returning to console, nvidia problem"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by fuscia on 2007-11-17
i have a very minimal setup (fluxbox, 9wm, no display manager). i have a nvidia card and installed nvidia-glx-new. everything's fine, except when i exit x, to get back to the console, the nvidia 'thing' seems to be still running and all i get is a black screen instead of a console. how do i exit this nvidia 'thing' so i can get back to the console?

---

### Post by taurus on 2007-11-17
How did you start X server?  Does your machine boot directly into GUI login screen or do you have to run **startx** to start fluxbox?

Otherwise, press <Ctrl><Alt>F2 to get to another console.

---

### Post by fuscia on 2007-11-17
i use startx to get into x. after i hit enter, this big, pretty nvidia screen opens and then, it goes to fluxbox. so, when i exit fluxbox, i guess i'm ending up in some nvidia world in between x and the console.

---

### Post by fuscia on 2007-11-17
ctrl+alt+f2 leads me to the same nvidian netherworld, but ctrl+alt+f1 then does not lead me back to my wm.

---

### Post by fuscia on 2007-11-17
i just did *sudo nvidia-glx-config disable* and it solved my problem without unsolving my screen resolution problem that i used it to fix in the first place. i rebooted and all seems well. ctrl+alt+Fwhatever gets me in and out of the console. all is right with the world. thanks for the help, yesterday and today.

---

### Post by Malibyte on 2007-11-17
> **fuscia said:**
> i just did *sudo nvidia-glx-config disable* and it solved my problem without unsolving my screen resolution problem that i used it to fix in the first place. i rebooted and all seems well. ctrl+alt+Fwhatever gets me in and out of the console. all is right with the world. thanks for the help, yesterday and today.

I have the same problem, but that solution won't work for me, as it disables the nvidia driver, which I need to use (running in SLi, and using MythTV, which doesn't handle HDTV-res video with the open nv driver).  

Any other ideas?

---

