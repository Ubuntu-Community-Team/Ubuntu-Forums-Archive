---
title: "installing applications"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by drmoore1 on 2008-04-02
Ok, so I'm trying to use the synaptic manager to download and install pidgin, but I get this:

pidgin:
  Depends: libatk1.0-0 (>=1.20.0) but 1.11.4-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.12.0) but 2.8.20-0ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.20.0) but 1.12.3-0ubuntu3 is to be installed

Then I went back and made sure I marked all the files I needed with it but then get this message:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to lock the download directory

How can I fix this? Thanks.

---

### Post by Lisa Y on 2008-04-02
open terminal and type

```

sudo apt-get install pidgin

```

It should automatically install those packages for you...those are the dependency's that pidgin needs

---

### Post by zvacet on 2008-04-02
System<admin<software sources>check all boxes under Ubuntu software and updates tab.Reload.In terminal 

```
sudo apt-get install pidgin
```

---

### Post by drmoore1 on 2008-04-06
Well I gave up and switched to 7.01 from 6.06, seems to work fine now.

---

