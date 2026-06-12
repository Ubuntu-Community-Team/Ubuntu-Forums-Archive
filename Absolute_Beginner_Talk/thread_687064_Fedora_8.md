---
title: "Fedora 8"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by koldphlame on 2008-02-03
"**I can't get flash to install in FF in edora 8**

[CENTER]:confused:[/CENTER]

---

### Post by Crafty Kisses on 2008-02-03
> **koldphlame said:**
> "**I can't get flash to install in FF in edora 8**

[CENTER]:confused:[/CENTER]

What's the error?

---

### Post by Crafty Kisses on 2008-02-03
First you need to become root, to do that, do the following:
```
su -
``` After you have become root, type the following: ```
yum install flash-plugin
```
Then you should have flash working.

---

### Post by jaytek13 on 2008-02-03
There are directions on this page about how to do various things with fedora, such as installing proprietary drivers:

[http://www.fedorafaq.org/](http://www.fedorafaq.org/)

And before you do a yum install flash-plugin, take note on the page that you have to add the livna repository first under the "setting up yum" section.

---

