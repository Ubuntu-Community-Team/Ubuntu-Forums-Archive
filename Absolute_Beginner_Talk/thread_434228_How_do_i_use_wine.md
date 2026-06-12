---
title: "How do i use wine?"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by thetechgeek on 2007-05-05
I have installed wine and everything, but it's not in the applications section, and when i try to get .exe applications to open with wine, the list of programs dosent list it...
I am confused...=P
(what's new?)

---

### Post by yabbadabbadont on 2007-05-05
[http://www.winehq.org/site/docs/wine-faq/index](http://www.winehq.org/site/docs/wine-faq/index)
[http://www.winehq.org/site/docs/wineusr-guide/index](http://www.winehq.org/site/docs/wineusr-guide/index)

If you still have questions after reading those, please post back here.

---

### Post by taurus on 2007-05-05
Maybe it's time to hit the documents, [http://www.winehq.org/site/documentation](http://www.winehq.org/site/documentation).

---

### Post by ubnewbie2 on 2007-05-05
Normally the .exe file type is associated with wine, so if you double click on an exe file, the system luanches it using wine (just like the way it plays a sound file or launches a spreadhseet).

Also, you can run it from the command line supplying the exe name as a parameter, e.g.

wine <appname>.exe

---

### Post by Acglaphotis on 2007-05-05
Eh i think you should try:

```
wine /path/to/exe/
```

-Acgla

---

### Post by thetechgeek on 2007-05-05
Okay, I got most of the wine stuff now, but i have one more question...
Where are the contents of things written if an installer saves them in C:\program files\whatever
?

---

### Post by taurus on 2007-05-05
Look in ~/.wine.

```
ls -la ~/.wine
```

---

### Post by jfinkels on 2007-05-05
> **thetechgeek said:**
> Okay, I got most of the wine stuff now, but i have one more question...
Where are the contents of things written if an installer saves them in C:\program files\whatever
?

Look in ~/.wine/drive_c/

---

### Post by yabbadabbadont on 2007-05-05
${HOME}/.wine/c_drive/.....

It may be drive_c instead of c_drive, I don't remember at the moment.

Edit: Operation "Overkill" is now complete.  :D

---

