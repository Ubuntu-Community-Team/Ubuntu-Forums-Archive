---
title: "splash ubuntu logo while loading gnome"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by alper_tr on 2005-06-29
Hi all,

I want to change that UBUNTU logo that splashed while loading Gnome.(not that login screen where we enter our user name and password) 
I checked around login secreen setup etc, however i failed)

I mean that rectangle shaped window that appears after entering the login info, that informs system gnome getting ready
I would be really glad if someone would help.

---

### Post by Xian on 2005-06-29
The easiest GUI method is to install gtweakui and then run the session command.
Open a terminal and issue the text listed below:

```
$ sudo apt-get install gtweakui
$ gtweakui-session
```

---

### Post by aysiu on 2005-06-29
You could also manually replace the image file with a new image. Just do a search for *ubuntu* in your filesystem. It's a .png somewhere like usr/share/pixmaps or something like that.

---

### Post by Ride Jib on 2005-06-29
Or, yet another way, without replacing files, or downloading new software would to be doing: Applications> System Tools> Configuration Editor

Then once it loads, / > apps > gnome-session > options.

Replace the path on "splash_image" to the location of your new splash image.

---

