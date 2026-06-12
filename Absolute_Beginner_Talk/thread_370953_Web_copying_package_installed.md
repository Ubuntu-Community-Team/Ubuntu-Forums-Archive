---
title: "Web copying package installed"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-26
Many thanks to all of you who advised me on installing a Web copier (httrack) . This is now installed (plus 4 dependencies - I am learning!)  . Now, how do I get it up and running ?   I have trying typing Httrack in terminal but to no avail.   All help much appreciated.

---

### Post by taurus on 2007-02-26
Try it with lower case h.

```
httrack
```

---

### Post by TonKi on 2007-02-26
> **ColinP said:**
> I have trying typing Httrack in terminal but to no avail.   All help much appreciated.
Did you also try **h**ttrack? That should do the job

btw webhttrack gives you httrack in a nice browser-window

---

### Post by Maestro23 on 2007-02-26
Remember: Case sensitive in linux.

---

### Post by ColinP on 2007-02-26
I have been using httrack but terminal reports errors such as : error whilst sharing shared libraries ' libhhtrack '.   Now I know how to install the package,, should I delete everything and restart ?

---

### Post by Maestro23 on 2007-02-26
> **ColinP said:**
> I have been using httrack but terminal reports errors such as : error whilst sharing shared libraries ' libhhtrack '.   Now I know how to install the package,, should I delete everything and restart ?

Worth a shot.

> sudo dpkg -P package name

Will purge everything including config files for the package.

---

### Post by ColinP on 2007-02-26
Many thanks,  Will delete package and start all over again !

---

