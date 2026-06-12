---
title: "Installing mutually dependent packages with GDebi"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by gcrussell1 on 2007-11-15
I'm trying to install OpenOffice.org 2.3 from debs I got from their site since I had a lot of crashing with the copy from Synaptic, but I'm running into the problem that the core packages are mutually dependent, and GDebi seems to only handle one package at a time, so I try to install core01 and it tells me it needs core02, but core02 needs core01, and so on. A brief search didn't seem to help, but it's probably a pretty simple solution. Anyhow, any help would be nice, as I'd like to get this up and running.

---

### Post by gcrussell1 on 2007-11-17
Seriously, does nobody have any idea? Maybe another program I can do it with? I've seen nothing in forum searches or Google searches that answered my question, but they don't just upload a major OSS project in debs without making it installable - what a waste of bandwidth if they did.

Bump

---

### Post by taurus on 2007-11-17
Why not just try using the wild card in place of the names?

```
sudo dpkg -i *.deb
```

---

### Post by gcrussell1 on 2007-11-17
I hadn't tried dpkg (because I didn't know about it and the pages and threads I searched up didn't mention it as an alternative for mutually-dependent packages). I ran it and selected all the packages like you suggested (except with the -iR tag to simply select the folder) and it installed perfectly. Well, it installed just as well as when I ran it from Synaptic and the Live CD - in that it installed and it works occasionally, but it generally crashes more than a trojan party on a Windows machine. I'm just about ready to give up on it until the next version comes out - until then there's always AbiWord... I don't use the other stuff much anyway, and I can always reboot into XP and use M$ Office if I need it.

---

### Post by kleo skywalker on 2007-11-18
You're right gcrussell1, OpenOffice is quite a pain, it crashes all the time.
Aren't there other office suites that work on Ubuntu?
And if not, then for basic functionality you can try Google Docs and Spreadsheets which added Presentations a while back.

---

