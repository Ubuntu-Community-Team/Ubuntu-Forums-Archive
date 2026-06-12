---
title: "Gconf-editor keeps settings of removed applications"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Average Joe on 2008-03-13
One of the problems I encountered when using MS Windows is its registry. After installing and uninstalling countless applications, the registry gets bloated and slows down Windows performance.

In Ubuntu, or rather Gnome, the "equivalent" of the Windows registry would be the [gconf-editor]("http://http://en.wikipedia.org/wiki/Gconf-editor"), where settings of all applications are stored. I recently noticed that after uninstalling several Gnome applications, some of them which I had never used, the settings are still present in gconf-editor. This leaves me with 2 questions:

1) When I remove an application, why are its settings not removed in gconf-editor?
2) Won't the conf-editor slow down my system on the long run like the Windows registry does? And if not, why not?

---

### Post by {BzF}~JOKesTER on 2008-03-13
Settings Are Stored There Unless You Uninstall The Apps With The --purge Extension.

It Won't Slow It Down As The Applications Only Access The "Registry" When The Run - It Uses A Set Path Technic That Does Not "Scan" Or "Look" Through The Registry For The Applications Entry But Rather Uses A Set Path.

I Hope This Info Helps!!!:)

---

### Post by thavid on 2008-03-14
worst than that is the fact that you can't delete the wireless profiles... For example, I've been around 10 diferent hot spots with this instalation, but I would like to delete some of this networks settings, so that my laptop would stop connecting to them as soon as it finds them...

---

### Post by ShodanjoDM on 2008-03-14
> **{BzF}~JOKesTER said:**
> Settings Are Stored There Unless You Uninstall The Apps With The --purge Extension.

It Won't Slow It Down As The Applications Only Access The "Registry" When The Run - It Uses A Set Path Technic That Does Not "Scan" Or "Look" Through The Registry For The Applications Entry But Rather Uses A Set Path.

I Hope This Info Helps!!!:)

Actually the gconf-editor still displays few subfolders of uninstalled programs, even if they've been purged. Not all, just few.

---

