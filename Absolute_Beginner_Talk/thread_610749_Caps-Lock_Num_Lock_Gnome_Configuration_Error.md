---
title: "Caps-Lock/ Num Lock Gnome Configuration Error"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by vodkacow on 2007-11-12
each time i hit caps lock or num lock, i get this error message:

An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly.

and when i click details:

Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-(none)/0/numlock_on": `(' is an invalid character in key/directory names

i will assume it's some kind of configuration file that is using (none) instead of my username, so can someone please direct me to that configuration file so that i can edit it??
thanks

i'm going a little crazy each time i hit caps lock or num lock....

---

### Post by CatKiller on 2007-11-12
I think that that's a GConf setting. The (none) should be whatever you called your computer when you installed Ubuntu (open a terminal window if you can't remember: Applications -> Accessories -> Terminal).

You can rename that key by renaming **~/.gconf//desktop/gnome/peripherals/keyboard/host-(none)/** to whatever it should be.

---

### Post by vodkacow on 2007-11-12
it seems that that key is named properly when look at it in terminal....

i am thinking that the configuration file is pointing to (none) instead of the correct name (as the files are all there and nameed correctly in that directory)

So, i am wondering what the coniguration file that is pointing to that directory is?
thansk

---

