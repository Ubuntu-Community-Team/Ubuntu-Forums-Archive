---
title: "how to remove software that has been compiled"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-06-23
How do I go about this?

It was the latest version of music-applet, but I want to use the old version that's in the repos.

How do I go about removing the compiled one?

---

### Post by raul_ on 2007-06-23
Sometimes it helps doing the same thing you do to install, but type "make uninstall" instead

Or just have a look at the readme file that was included in the source code

---

### Post by bodhi.zazen on 2007-06-23
The only other thought is to look at checkinstall

This converts your source to a .deb which is easier to uninstall later. 

Checkinstall sometimes has issues though :(

---

### Post by quincy_the_penguin on 2007-06-23
Did you keep the folder that you installed it from?  If so, cd into it and run "sudo make uninstall".

---

### Post by RedSquirrel on 2007-06-23
> **moredhel said:**
> How do I go about this?

It was the latest version of music-applet, but I want to use the old version that's in the repos.

How do I go about removing the compiled one?


Did you use checkinstall or just plain "sudo make install"?

If you created a deb package and installed that, you could remove it with

```
sudo dpkg -r package-name
```If you did "sudo make install", try "sudo make uninstall" to remove. If for some reason "sudo make uninstall" is not available then see what was installed:

```
make -n install > make_install_log.txt
```and remove those things manually.

---

### Post by r4ik on 2007-06-23
Might be wrong here but maybe,

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)


Good luck !

---

### Post by energiya on 2007-06-23
It helps to have a source manager like paco.

---

### Post by moredhel on 2007-06-25
luckily I kept the folder and sudo make uninstall worked :D

Thanks all :)

---

