---
title: "Changed monitor type now no video"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by wardjame on 2008-04-15
Hi all,
Just switched over to ubuntu for my media pc attached to a plasma tv via a vga cable.  Everything was working fine until I went to tweak the video settings.

I changed my monitor type to Widescreen LCD monitor and logged out.

Now I get the login screen and as soon as I log in my screen goes black but i can hear the sounds.  I'm guessing my mistake was setting it to LCD since it is probably looking for a digital out now instead of the vga cable I am using.  How can I set this back to the default monitor settings from the command line and get my system back up and running?

Cheers!

---

### Post by spiderbatdad on 2008-04-15
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

logout...login

---

### Post by wardjame on 2008-04-15
sweet.  I'm back in action.  Thanks for the quick help.

---

