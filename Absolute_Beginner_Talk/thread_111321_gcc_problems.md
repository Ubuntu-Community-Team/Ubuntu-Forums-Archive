---
title: "gcc problems"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by proventech on 2006-01-02
Help!  I'm another newbie using Linux :smile: and I'm trying to install ksmoothdock.  When I run ./configure it gives me the error below.

checking for x... configure: error: can't find x includes.  Please check your installation and add the correct paths!

Any help is appreciated.

---

### Post by xtacocorex on 2006-01-02
It seems that you are missing the X11 library files.

```

sudo apt-get install xlibs-dev

```

---

