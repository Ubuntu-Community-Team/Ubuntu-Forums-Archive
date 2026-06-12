---
title: "Help! Log-in screen wont load!"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by DMBrazil on 2007-11-24
I've been trying to get compiz to work and following some directions in the forums I cannot get into my laptop.

I changed my driver from vesa to i810 in xorg.conf file.

After i changed that, my login screen would only load after my computer would freeze and overheat (weird i now). 

Then i change my driver from i810 to intel in xorg.conf file.

Now it wont load at all. I get the "Low graphics warning" and wont load.

What can i do?!?
 is there a way to change my harddrive info by using the terminal off booting the install cd?

---

### Post by taurus on 2007-11-24
Wait for your machine to finish booting.  Then, press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password and reconfigure your X server again with

```
sudo dpkg-reconfigure xserver-xorg
```
When you are done with it. See if the new version works by getting back to the GUI login screen with <Alt>F7.  Now, restart X with <Ctrl><Alt>Backspace.

---

