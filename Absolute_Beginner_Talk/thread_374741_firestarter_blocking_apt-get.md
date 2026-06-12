---
title: "firestarter blocking apt-get"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by balloons on 2007-03-02
I can't apt-get update. I have to turn off the firewall for it to work.  When have firestarter running, it shows a hit from forester.canonical.com as well as prat.canonical.com. No matter what I allow, firestarter still shows a hit and I get a time out from the server. I am at a loss as to why the repositories servers would trigger such action now, when nothing has changed on my end. Here's a copy of my sources.list. Does anyone know why my firewall would be blocking updates, or what to do to fix?

```

deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu edgy-commercial main 
# deb http://archive.ubuntu.com/ubuntu/ feisty universe main multiverse restricted

```

---

