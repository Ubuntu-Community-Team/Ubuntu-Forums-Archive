---
title: "where did my files go?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by aquintz09 on 2008-01-23
if ever i download something, lets say a driver, where can i find its location so i can manually delete it? and how will i know how much memory i have consumed in my hard drive? i already went to the system monitor, file manager, but still couldn't find it. thnkz..

---

### Post by emrahustun on 2008-01-23
downloading with firefox?
if yes, there is default download folder. you can see and edit from firefox settings menu.

---

### Post by gvartser on 2008-01-23
It depends, but if you are using Firefox and didn't change the default download location all downloaded files should be stored on your desktop.

/G

---

### Post by PeterJS on 2008-01-23
> **aquintz09 said:**
> if ever i download something, lets say a driver, where can i find its location so i can manually delete it? and how will i know how much memory i have consumed in my hard drive? i already went to the system monitor, file manager, but still couldn't find it. thnkz..

Manually deleting things is generally a bad idea, leaves the system in an inconsistent state, generally it's best to uninstall things with apt or synaptic.

Here's the wiki page on where things are:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
And here's the complete standard if you really want details, or questions about some of the more exotic subdirectories:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

For disk usage try this in a terminal:
```

df -h

```

---

