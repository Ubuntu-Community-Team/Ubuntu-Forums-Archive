---
title: "Gxmessage install - can't find GTK?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by bluedeer on 2006-12-24
I'm trying to install gxmessage so that I can get a popup window from Remind whenever I log in.  At first when I'd run ./configure, it would say it couldn't find make.  I installed make and build-essential and tried again.  Now, it's getting a little farther, but it's giving me the following errors:

checking for gtk+-2.0 >= 2.6... Package gtk+-2.0 was not found in the pkg-config search  path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_ PATH environment variable No package 'gtk+-2.0' found

configure: error: Library requirements (gtk+-2.0 >= 2.6) not met; consider adjusting th e PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so  pkg-config can find them.

I have absolutely no idea what this means, as I've only been using Ubuntu for a week.  Can anyone help with this error?

I did some searching for info about this error and found a site that said something about setting the pkg-config path by doing the following:

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
export PKG_CONFIG_PATH

I did both of those in the terminal, but it didn't seem to help.  (Also, if that was incorrect, can someone let me know how to switch it back to whatever it was supposed to be?)

Thanks!

---

### Post by bluedeer on 2006-12-24
Ok, I did even more digging and figured this out...gxmessage is now installed and working.

Just in case anyone else comes across this thread while searching for the same error message I was getting, all I had to do was install libgtk2.0-dev (and its dependencies) through Synaptic.

---

