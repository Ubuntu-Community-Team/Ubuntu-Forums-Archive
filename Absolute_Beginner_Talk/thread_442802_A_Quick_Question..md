---
title: "A Quick Question."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-13
I know I've read this here somewhere before, and even did a search with no results.
How do I refresh or reload my gnome desktop? or rather, what is the command?

Dr Small

---

### Post by overdrank on 2007-05-13
> **Dr Small said:**
> I know I've read this here somewhere before, and even did a search with no results.
How do I refresh or reload my gnome desktop? or rather, what is the command?

Dr Small

Hi ctrl,altl,backspace will restartX
Hope that is what your where looking for!:popcorn:

---

### Post by Martin on 2007-05-13
Ctrl Alt BAckspace will restart the X server - if thats what you mean

---

### Post by bobplano on 2007-05-13
to restart X you can just press control+alt+backspace. there's also something like sudo /etc/init.d/gdm start which i assume you can just use restart instead of start

---

### Post by Dr Small on 2007-05-13
Ok. Thanks guys. That helped ;)
I had run gdesklets and it locked up, leaving gray blocks on my desktop I couldn't get rid of....
Thanks again ;)

Dr Small

---

### Post by nonewmsgs on 2007-05-13
is that bad for X?  it looks very violent and if it is bad, is there a way to reset x ie. make it accept the changes you did to xorg.conf?

---

### Post by bobplano on 2007-05-13
its kindve like restarting your computer except your just restarting the GUI. its not bad and if it is then i would be in trouble. the ctrl+alt+backspace should work to have your newest xorg changes shown

---

### Post by tgalati4 on 2007-05-13
It's bad in that it will close any open applications.  Be sure to save your work and shut down anything important.  Think of it as a mini-boot.  It basically closes anything that is open, restarts the xserver, then the window manager (probably gnome in your case).  I've experienced similar problems with desklets.  Sometimes they don't get redrawn properly.

---

