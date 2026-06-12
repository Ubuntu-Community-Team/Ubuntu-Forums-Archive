---
title: "Wine whine"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2006-08-05
I've been using Ubuntu for a little over a month now, and am really pleased with it.  I enjoy having the kind of control  it gives me with relatively little effort.

But I've come to the point of evaluating whether I can use it as my only OS on one particular computer, and there are a few areas which aren't covered as completely in Linux as they are in Windows... so I just installed the Ubuntu version of Wine.

My only question is, now that I've installed it, where is it?  There's no real category it can come under, so I just searched in all of them and didn't find it.

Anybody know how to find Wine on the computer once it's installed, and run it?

Thanks!

-Mark

---

### Post by shanepardue on 2006-08-05
wine creates a "c drive" in your home folder that is hidden until you allow to view the hidden files and folders.

to configure wine, type "winecfg" in the command line.

hope that helps a little!!

---

### Post by Jagot on 2006-08-05
You need to run winecfg in the terminal to configure it first.  Now thats done, you can run a Windows file like this:

```
wine /location/of/file/filename.exe
```

---

### Post by mjpatey on 2006-08-05
Nice!  Thanks a lot, folks.

-Mark

---

