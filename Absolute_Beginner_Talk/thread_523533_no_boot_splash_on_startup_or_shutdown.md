---
title: "no boot splash on startup or shutdown"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by kmcq on 2007-08-12
i have a dell latitude c400 running ubuntu feisty 7.04, when i fire it up i see the Dell logo and the bios logo, followed by "startup up please wait..." at first this text appears in what i blieve is 'system' font then switches to courior font and abruptly disappears, the screen remains on and displays nothing but black for  roughly 90 seconds and then the login screen appears, on shutdown, essentially the same thing happens, i hit shutdown, many lines of disperportioned console text appear (what seems to be the output of kernal executing the shutdown process) all at once then disappear after about one second, the screen goes black for about 30 seconds, then it cuts the power 

any ideas on how to solve this (by the way this is a fresh install, this also happens when i load ubuntu via live cd)

---

### Post by meierfra on 2007-08-12
I had a similar problem on also on a dell.  I ignored it, but just a couple of weeks ago I accidental run across   a solutions while searching for some else:

At boot up enter  the BIOS setup via F12:

go to 'Integrated Devices',

then to 'Onboard video buffer'. 

Change it from 1Mb to 8Mb.

---

### Post by kmcq on 2007-08-12
hm ok ill check that out, thanks for the tip (ill edit this post later and let yall know if it worked or not)

edit: no luck, my bios is dell version A10, i cant seem to find the onboard video buffer option or an Integrated devices menu, any advice?

---

