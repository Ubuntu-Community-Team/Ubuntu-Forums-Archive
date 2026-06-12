---
title: "aticonfig &quot;screen0 does not exist&quot;"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by nittanylion on 2007-10-18
(sorry if double, couldn't find answer)

I've been trying to get Gutsy to cooperate with my monitor for awhile now, and finally remembered about aticonfig --resolution. However, whenever I use:

sudo aticonfig --resolution=0,1440x900,.....

I get the message: "error as set screen resolution : screen0 does not exist \ aticonfig: parsing the command-line failed"

any ideas?

fglrxinfo:
display: :0.0 screen: 0

Sorry for edit by the way, was working on a few issues and forgot I had filled out part of the form

---

### Post by nittanylion on 2007-10-19
*bump*

I don't know if it helps, but if I manually add "1440x900" into xorg.conf, the bottom 5th of the screen becomes distorted and unusable. I seem to recall similar issues in Feisty where I could *only* get the 1440x900 resolution to work correctly by using aticonfig --resolution.

---

### Post by nittanylion on 2007-10-19
*last bump*

I find it weird that aticonfig gives an error message, which apparently no one knows how to solve (I'm including google search in this)

If it's not on my end, I guess it's just a bug in Ubuntu then...

---

### Post by corpsicle on 2007-10-19
I get the exact same thing. Radeon 9800 pro and it worked fine with the resolution manually inserted in xorg.conf, however after upgrade to 7.10 it doesnt seem to care about my resolutions.
And ive checked that the xorg.conf is unaltered.
It DID ask me if i wanted to install ati drivers, and i agreed, and after reboot it confirmed that the driver was installed.

---

