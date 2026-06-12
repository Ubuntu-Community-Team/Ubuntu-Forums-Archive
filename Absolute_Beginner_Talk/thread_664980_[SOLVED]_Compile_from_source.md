---
title: "[SOLVED] Compile from source"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Faud on 2008-01-11
Can someone please link to me a site that explains how to compile something from source. Thank you.

---

### Post by eapache on 2008-01-11
I can give you a brief tutorial. Any particular program?

---

### Post by Faud on 2008-01-11
The new WINE, yes I know that it will be in the repos probaly tomorrow but I would like to try it.

---

### Post by eapache on 2008-01-11
You'll need a lot of development packages and compiler packages etc. to do that, so I suggest waiting, however if you must, install the 'build-essential' package as well as the stuff here: [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

There is a shell script that will download everything for you.

---

### Post by Faud on 2008-01-11
Thank you for the suggestion but this must be above me atm. I have two downloads now and absoutly no idea what to do wtih them lol

---

### Post by capink on 2008-01-11
There is one command to install all the build dependencies ( dev packages )

```
sudo apt-get build-dep wine
```

This will install all the build dependencies for the version in the repositories. Those build dependencies usually works with later versions as well.

---

### Post by jken146 on 2008-01-11
monkeyblog.org/ubuntu/installing/

---

### Post by oldos2er on 2008-01-11
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

