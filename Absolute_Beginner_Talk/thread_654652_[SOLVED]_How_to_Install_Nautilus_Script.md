---
title: "[SOLVED] How to: Install Nautilus Script"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by b0rka7a on 2007-12-31
OK, I know this may be a stupid question, but how can I get this script to work:
[http://gnome-look.org/content/show.php/Send+to...?content=67627](http://gnome-look.org/content/show.php/Send+to...?content=67627)
I want to have that script when I right-click on a folder/file.

---

### Post by twiceasworn on 2007-12-31
well since I can't untar the english version from that link I can't tell you specificly how to go about making it.  However, typically when you get source files like this there is a configure script you use which creates a makefile which allows you to install.  So usually its something along the lines of 
```

./configure
make
sudo make install
```

---

### Post by b0rka7a on 2007-12-31
Inside the archive is a folder source, but in this folder I see only one script file (named "Send-to"). So there is nothing to configure.
But one a minute ago, I found out how to install Nautilus Scripts: place the script in ~/.gnome2/nautilus-scripts and it worked :) Thanks for the reply. See you next year :P

---

