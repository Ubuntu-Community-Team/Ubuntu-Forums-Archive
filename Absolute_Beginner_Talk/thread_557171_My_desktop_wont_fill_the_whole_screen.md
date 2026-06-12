---
title: "My desktop wont fill the whole screen"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by hbarnes2424 on 2007-09-22
Hello guys!  I am a newbe to all of this so please excuse my ignorance.  I installed Ubuntu (the education version) yesterday on my Dell inspirion 1100 (yes I know it is old but it was free!)  Anyway, when I completed the instillation the screen only takes up a third of the whole screen.  It seems to be centered on the screen.  I went in and tryied to make it stretch but it didn't work.  Any ideas?

---

### Post by 505 on 2007-09-22
Usually this is a laptop issue, not a software issue. Most laptops have such a feature to easily connect it to a beamer running on a low resolution.
There is a key combination to restore the resolution to full. Usually this is Fn+(some F key) The Fn is usually lower left, near Ctrl, and the F key usually has a small screen on it.

---

### Post by arochester on 2007-09-22
> Ubuntu Breezy Installation Notes

Ubuntu installs and mostly just works on the Inspiron 1100 (networking, hibernate, synaptics, sound etc). However, the xserver installation isn't configured correctly. Use this xorg.conf file instead. Copy it to /etc/X11/xorg.conf and reboot. Thanks to Micah Cochran for supplying this fixed xorg.conf



From [http://www.geocities.com/randomnumbergenerator2001/](http://www.geocities.com/randomnumbergenerator2001/)

---

### Post by hbarnes2424 on 2007-09-22
Ok, remember I am new!  How do I do that?

---

