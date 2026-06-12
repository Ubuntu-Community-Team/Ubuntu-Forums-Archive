---
title: "how to modify registry settings in wine?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by lintroduccion on 2006-12-14
I'm running Xubuntu Edgy 6.10 (i386) on my system.

The problem is that I want to run a windows program, already installed on my shared (fat32) partition from my windows xp session. I erased the installation program, as I saw the program itself didn't need any extra dll files but some registry entries which I have them exported in a *.reg file. When I tried to run it with wine, it complained that registry settings are missing and refused to run, obviously, and I don't know how to apply my .reg file to the program so it runs without problem.

Is there a way to... manually modify wine's "registry", if it does exist? What does wine do with windows registry and dlls... store them in a special path?

---

### Post by hollaburoo on 2006-12-14
just use the command regedit

---

### Post by lintroduccion on 2006-12-15
Thanks!

...I guess I need more common sense before anything.](*,)

---

### Post by dserver on 2008-07-06
I think you just hit something. The hack has an .exe file but also a .DLL file, which I think may be the problem. Is there anyway to edit how Wine uses a DLL file?

---

