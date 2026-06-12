---
title: "I'm paranoid"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by kane77 on 2006-12-13
I just did a very stupid thing. I removed few programs (e.g. firefox, Open Office etc..) I installed them back again and since then I'm paranoid that I messed something up... Dont know why... maybe because I started firefox from cli and I saw couple of warnings about libpangohack.so... 

Can you tell me that my ubuntu is OK?

and second question... is there a way to remove old and unnecessary files (mostly leftovers from previously installed programs) etc?? (how do I know they are unnecessary?

---

### Post by IYY on 2006-12-13
I'm pretty sure everything is fine. For future reference, after deleting some installed-by-default packages you can reinstall everything by removing and adding the ubuntu-desktop metapackage.

---

### Post by earobinson on 2006-12-13
linux is very adaptable and designed to remove and add in packages without a hiccup, so on that end i'm sure everything is fine.

In terms of uninstalling unused packages the apt support for this is currently not very good afaik

---

### Post by muep on 2006-12-13
If you install something with Ubuntu's package managemet tools like Synaptic or Apt, you will get all the necessary packages to run them, too.

The ubuntu-desktop metapackage is a good way to ensure that all the usual Ubuntu stuff is installed.

---

### Post by kane77 on 2006-12-13
the packages installed via synaptic or apt-get can be removed easily (and I believe they dont leave much of a mess...) but I dont know how in the world would I uninstall something I compiled from source...

---

### Post by user1397 on 2006-12-13
in the future, when installing stuff with the CLI, you could use aptitude instead of apt-get, which remembers all dependencies for a program, and hence removes everything, no (or almost no) leftovers.

and btw, uninstalling things from source depends on if the packager provided an uninstall file in the source.  if there is one, you could do this:
```
cd /path/to/source/folder/
sudo make uninstall
```(thats if you installed it with **sudo make install**)

---

