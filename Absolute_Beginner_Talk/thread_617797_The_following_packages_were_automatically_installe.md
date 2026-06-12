---
title: "The following packages were automatically installed and are no longer required:"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-19
That's what "apt-get" is telling me every time I update or install packages.  It lists 13 packages, mostly having something to do with java.  My problem is...  I don't know if apt-get is telling me the truth! >.<

Seriously, though, is apt-get generally "right" about me not needing files any more?  I just thought it would be good to ask before I ran the auto-remove it suggests.  The packages are as listed:

libbcprov-java libglib-java libcommons-cli-java libgtk-jni libglib-jni libgnucrypto-java libswt3.2-gtk-java libcairo-jni libcairo-java libgtk-java liblog4j1.2-java libswt3.2-gtk-jni libseda-java

---

### Post by SunnyRabbiera on 2007-11-19
I think its the way gutsys packages work, I get this too.
there might be a goof somewhere in the way gutsy packages things, as this never happened in older versions.
I dont think there is anything wrong, as this seems to be a minor annoyance

---

### Post by Paul820 on 2007-11-19
Yes, apt is usually right. If you have uninstalled something in the past the dependencies usually get left behind. Any dependencies that are needed by other programs will not be in that list so you can remove them. They will not be deleted from your system, the .deb packages are still stored in /var/cache/apt/archives so if anything does ( not likely ) go wrong you can just as easily install them again. If you are worried, write down the names and put them back if something happens. But, like i said, it should be fine, don't worry. :)

---

### Post by kevind23 on 2007-11-19
apt-get is the system used by Ubuntu for managing Debian packages from one or more central repositories.

If you're not using any of those packages, which you aren't (since apt-get wouldn't tell you to remove them if you are), then you are safe to remove them with the command **sudo apt-get autoremove**. There is nothing wrong and this listing is just to help you free up extra packages you aren't using :-)

---

### Post by Sarteck on 2007-11-19
Thanks all.  Had a feeling that was the case, but I just don't want to screw things up on this end after I finely got it working nicely.  XD

---

### Post by Paul820 on 2007-11-19
If you use **sudo apt-get remove** package name, it will only suggest that other packages that were it's dependencies need to be removed. If you use **sudo aptitude remove**, it will remove them automatically.

---

### Post by aysiu on 2007-11-19
Unlike Windows' dll warnings (which are generally meaningless), the *apt-get* prompt to remove no packages no longer required can usually be heeded (in other words, those packages are probably not needed any more).

The best part is, unlike Windows, it's easy to reinstall those packages if you find they are critical.

---

