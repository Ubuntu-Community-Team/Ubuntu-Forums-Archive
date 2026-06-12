---
title: "weird quirk"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by ubntu350 on 2008-01-30
Been running Ubuntu for about a week now, two days ago the OS stopped letting me move open windows around.  Anyone else have this problem? Suggestions?

---

### Post by jordanmthomas on 2008-01-30
Does holding alt let while click-dragging work?

Also, are you running compiz (called desktop effects in Ubuntu I think)?

```
metacity --replace
```
should fix you up for the time being until you figure out what's wrong.

---

### Post by ubntu350 on 2008-01-30
I am running desktop effects, and no it makes no difference if I hold alt while click dragging, still won't let me move any windows.  Interesting sidenote, while in expo mode I can move the windows, just not while in normal view mode.

---

### Post by jordanmthomas on 2008-01-30
Perhaps you don't have the "move" plugin enabled in the settings manager?
It may sound dumb, but the solution is usually something you overlook.

Or, perhaps, you've bound move to some strange key.  Look around in the compiz settings and you may find your problem

---

### Post by ubntu350 on 2008-01-30
You nailed it, it was the move plugin in the desktop effects preferences. Put it in the enabled list and that did it.  Thank you!

---

### Post by ubntu350 on 2008-01-30
I have another question.  I am very new to Linux, I'm just learning how everything works.  One thing that is confounding me is how to install programs.  For instance, I have downloaded Avant window manager into tmp, however I am xp narrowminded.  Is there an executable install file, nothing I click on does anything, and the package manager can't find anything?? Could you school me in the ways of installing in linux

---

### Post by jordanmthomas on 2008-01-30
This is a good read I think:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

Also, the "exe" of Ubuntu (it's not really even close, but whatever) is the .deb file.  If you want windows-like installers, try getting some things from [http://www.getdeb.net/](http://www.getdeb.net/)

Mostly though, installing things is done in system --> Administration --> Package manager.  It's very easy once you get used to it.  

What kind of file did you get for Avant window navigator?  If it's a .tar.gz, it's likely the source code.  This is not really that hard to compile and install, but it IS much more involved than finding a precompiled deb or using the package manager (avant might not be in there though...I am not sure)

---

### Post by oldos2er on 2008-01-30
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ubntu350 on 2008-01-30
seems pretty straight forward.  Synaptic can't find the package I downloaded though. Im sure there's a box in a menu somewhere that will fix that.

---

### Post by jordanmthomas on 2008-01-30
Synaptic downloads files for you.  It will not find the package you downloaded to /tmp.

---

### Post by emarkd on 2008-01-30
If you're trying to install AWN, here's the official guide from Avant:

[http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu](http://wiki.awn-project.org/index.php?title=A_Visual_Install_Guide#Ubuntu)

---

