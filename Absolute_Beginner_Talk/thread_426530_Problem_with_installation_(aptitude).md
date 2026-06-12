---
title: "Problem with installation (aptitude)"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by sessine on 2007-04-28
When I am installing programs via aptitude I have recently started to get the following 'error' message at the setting up ... stage:

```
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!

```

the man page for kbuildsycoca says it rebuilds the system cache.  Have I done something to mess up my cache?

---

### Post by jargoman on 2007-05-04
try this

$ sudo apt-get update

this refreshes your database
then proceed as normal

---

