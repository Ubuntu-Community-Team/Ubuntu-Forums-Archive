---
title: "xserver off and no desktop"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by gulmer on 2007-06-13
I did a reconfig of the xserver and must have screwed something major. Now when I turn on the computer I get a screen with the message the xserver is off and needs to be reconfig,that it was misconfigured, error: NI not implemented(unknown)
Then I get into a screen telling me about ubuntu being free software etc, and absolutly no warranty etc.,then a command line and I have no idea what to put in to get my desktop back.Help:sad:  The whole screen looks like one large terminal.

---

### Post by diatribe on 2007-06-13
you need to replace whatever files you edited with the backups you (hopefully) made.  what exactly did you do when you 'reconfigured' the xserver

---

### Post by gulmer on 2007-06-13
> **diatribe said:**
> you need to replace whatever files you edited with the backups you (hopefully) made.  what exactly did you do when you 'reconfigured' the xserver

I just ran the set up and answerd the questions about keyboard,monitor,video card,and mouse. I just got into the reconfig xserver and ran the set up again,and I beleive the first time I did it I put the wrong video card memory in, which ask for kb instead of mb and my conversion was off the first time, this time it is right. Now I finished the reconfig and the screen still wants a command and I have no idea what it wants now.

---

### Post by diatribe on 2007-06-13
try typing either startx or gdm, that should bring you into X; barring that try control+d

---

