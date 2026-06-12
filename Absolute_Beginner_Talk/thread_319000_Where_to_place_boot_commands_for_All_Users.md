---
title: "Where to place boot commands for All Users"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by SonWon on 2006-12-14
I just finished reading How Linux boots and found it very interesting and informative. One question I have that was not covered is where should I place commands that are hardware specific? Like,

> # set Left-scroll to act like Left-arrow
setkeycodes 5a 105

# set Right-scroll to act like Right-arrow
setkeycodes 59 106

# set Up-scroll to act like Up-arrow
setkeycodes 69 103

# set Down-scroll to act like Down-arrow
setkeycodes 68 108


These commands will enable the 4-way scroller on my laptop. I would like these commands to be non-user specific but I am also interested in knowing where to place user specific commands?

Thank you for the help.
SonWon

---

### Post by SonWon on 2006-12-17
I saw one website that hinted that these commands would go in the xorg.conf file.  Does anyone know what section of the file?

Thanks,

---

### Post by moshuptrail on 2006-12-17
If you go to System > Preferences > Keyboard Shortcuts, you might be able to just define it there.  Where the GUI puts it?  I'm not sure.

If not, you might be able to put something (anything) there and then look at the xorg.conf file to see where it went.

---

