---
title: "I broke Firefox"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by matrisking on 2007-02-27
Hey all,

My Firefox was acting funny... it was suddenly closing with no errors.  So I tried to follow a guide to upgrade to firefox 2 and ended up breaking it entirely.  I ran the following script that I got from a HOWTO:

[http://lamparder320.googlepages.com/firefox2.txt](http://lamparder320.googlepages.com/firefox2.txt)

Now, whenever I try to run firefox, it just pulls up the "thinking" cursor icon for a few seconds and then does nothing.  I tried updating from the package manager (something I should have tried first, probably), no help.  Rebooted, no help.

Any ideas?

Thanks in advance!

---

### Post by taurus on 2007-02-27
Try to run it from a terminal to see what's the error is.

```
firefox
```

---

### Post by crossedout on 2007-02-27
Try deleting the profile and creating a new one.  Or if you are really attached to your bookmarks/settings etc. backup them up first.

-Xout

---

### Post by matrisking on 2007-02-27
> **taurus said:**
> Try to run it from a terminal to see what's the error is.

```
firefox
```

Invoking from terminal gives this error:
/opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I'm guessing i need to install this, but when I try to get libstcc++5 via apt get it asks for me to insert the 5.10 ubuntu cd... which I do not have remotely handy... is it possible to install this without the cd?

---

### Post by taurus on 2007-02-27
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the the line that has CDROM in there, usually the first line.  Save it and run

```
sudo aptitude update
```
Now, install whatever you want.

---

### Post by matrisking on 2007-02-27
You are my hero, worked like a charm, thanks!

---

