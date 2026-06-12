---
title: "Help! My Xserver is jacked up :("
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-05-06
ok, here's the deal: i have had ubuntu installed on this computer for about 2months and tonight, after i felt like playing with themes, namely LiNsTa3, my xserver just crashed. i can log back in, but all i get is a blank screen. i do have control as i can rotate my beryl cube. i can also log in and start a session via recovery mode, but i really don't know where to look for this problem. I have no icon's or bars or anything other than a mouse. please help!

---

### Post by Tundro Walker on 2007-05-06
I probably won't be able to fully help you (still a bit of a Linux noob myself), but here's some thoughts.

 If it's an Xorg issue, let it boot up as normal, then **CTRL+ALT+Backspace**.  This basically "reboots" the desktop manager without actually rebooting Linux.  What should happen is it'll kick you back to a login screen.  From there, you should have some dropdown menu options letting you choose a different desktop manager.  Try choosing "safe" mode or some-such.  That should let you log back in to a pretty bare or default desktop setup, letting you at least get in and correct what's hosed up.

Once you hit a desktop, you can try uninstalling the theme you were messing with.  Or, go to "(Start) > System > Administration > System Log" and check out your "Xorg" log file.  You should be able to spot some errors in there when it hosed up on last boot.  If you post the error messages, some folks (more knowledgable about Xorg than me) should be able to help.

---

### Post by totalnub on 2007-05-06
thanks for the reply although this post exactly was what happened. FIXED NOW :)

edit: forgot link lol   [http://ubuntuforums.org/showthread.php?t=409155](http://ubuntuforums.org/showthread.php?t=409155)

---

