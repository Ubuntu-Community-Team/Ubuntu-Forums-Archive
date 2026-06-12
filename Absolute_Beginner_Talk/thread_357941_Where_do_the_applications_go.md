---
title: "Where do the applications go"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by tjtansey on 2007-02-10
OK I know there is no such thing as a stupid question, but where do applications get installed?  I've notice that many don't end up in the menus, and I know how to edit the menus, but I guess the question is:  what is the equivilent of "Program Files?"

---

### Post by taurus on 2007-02-10
Most of them are resided in /usr/bin.  

```
whereis **program**
```

---

### Post by tjtansey on 2007-02-10
Thanks, also not related to my preious post, but is there a disk error checking utility out there?

---

### Post by Jussi Kukkonen on 2007-02-10
There's no such thing as Program Files -- documentation goes into one place, logs to another, config files to yet another and so on. 

If you are looking for the executable and know the name, run ***locate <executable-name>*** (you might have to run ***sudo updatedb*** before that if you just installed the package.  

If you are looking for the executable but don't know the name, you'll have to use dpkg-query (or synaptic or packages.ubuntu.com). This will almost always list some good candidates:
***dpkg-query -L <package-name> | grep bin***

---

### Post by mcduck on 2007-02-10
Best search tool for this purpose is 'which'.

Running 'which programname' returns full path to the executable file of app called 'programname'.

```
$ which firefox
/usr/bin/firefox
```

Anyway, in most cases you'll find the executable from /usr/bin.

---

### Post by pay on 2007-02-10
> **tjtansey said:**
> Thanks, also not related to my preious post, but is there a disk error checking utility out there?It should check every 20 mounts automatically.

---

### Post by tjtansey on 2007-02-10
> **pay said:**
> It should check every 20 mounts automatically.

wow didn't know that.
Thanks

---

