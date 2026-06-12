---
title: "Xserver won't load"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Onwlyix on 2007-08-13
Hello! Another problem. I just installed Ubuntu 7.04 for the fifth time (fifth attempt), but this time with Wubi. The thing is, it won't start the X Server. When I start up Ubuntu, it starts loading, but then I get the blue/gray screen of not-workingness telling me Xserver (your graphical interface) blah blah blah. I've tried "Sudo dpkg-reconfigure [with and without -phigh] xserver-xorg" before, but it still didn't work. And now, when I start up Ubuntu, and after the error, it doesn't even let me run commands. It goes to the black screen, but it doensn't do anything. It doesn't ask for a login, and nothing happens when I type anything, so I can't try anything else. As a side note, I had the same problem with the LiveCD, but I fixed it by running it in safe graphics mode. What should I do?

---

### Post by loserboy on 2007-08-13
it's most likely an issue with your video card, and will be easier to fix with a real installation that with wubi, at least I think more people will be able to help you than with wubi.

what's your video card anyway

---

### Post by Hospadar on 2007-08-13
When you get to the error, what happens if you do ctrl-alt-F1 (to go to a text terminal)  Also, could you post the detailed error message when that happens (I think it asks you to see detailed x-server output and then there will be two screens, the first of which Is the more useful).

---

### Post by Onwlyix on 2007-08-13
Now when I start up, it freezes at about 1/6th through the loading bar. Then it loads "Busybox," and it won't do sudo or anything. Ctrl Alt F1 does nothing either now. Soo, this keeps getting worse. I think Ubuntu hates me.

Loserboy, my vdieo card is an ATI Radeon 9250

---

### Post by Hospadar on 2007-08-13
I think at this point you should try installing off the livecd as opposed to wubi.  your card shouldn't be giving you problems like that, so I would bet that this is an installation problem.

---

### Post by nvrpunk on 2007-08-13
try "sudo xorgconfig" 

it should ask some questions and configure your Xorg for ya.

---

