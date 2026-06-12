---
title: "How do I get the cool desktop effects?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by rock0nman on 2007-12-15
I just installed Ubuntu 7.10 and want my desktop to look similar to this...
[http://www.flickr.com/photos/wfpearson/499550338/]("http://www.flickr.com/photos/wfpearson/499550338/")

But my own backgrounds of course.   I need a step by step.  I know there's another program i need to install.  I've already ran the update program and installed nearly everything on the internet.  But i want the cube..and stuff.   HELP PLEASE!!!

---

### Post by Ub1476 on 2007-12-15
Install Advanced Desktop Effects:

```
sudo apt-get install compizconfig-settings-manager
```

Open System>Preferences>VIsual Effects>Select "Custom".

Open System>Preferences>Advanced Desktop Effects

Select "Cube and "Rotate cube". Go to General Settings and change desktop size to 4.

To run cube, press CTRL+ALT+Mouse button1 (key settings is in the "actions" tab in the plugin settings).

If you can't enable Visual Effects, post the output of:

```
lspci | grep VGA

compiz --replace
```

---

### Post by rock0nman on 2007-12-15
Some of your specifics didn't apply to me for some reason but you got me on the right track.  Thanks a bunch.   This is quite a learning experience.

---

### Post by alsamman on 2007-12-15
just remember that you have to install Compiz, NOT Beryl, beryl is a dead project and is quite unstable. Compiz works great

---

### Post by Ub1476 on 2007-12-15
Sorry, maybe  I should have made it more clear. You got it working, right?

---

### Post by rock0nman on 2007-12-16
Yep i got it up and working pretty good till i tried to enable the widget layer.  Now i can't even open a window.   Is there a way to disable the widget layer through the terminal?

---

