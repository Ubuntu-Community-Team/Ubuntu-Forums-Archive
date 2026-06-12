---
title: "[SOLVED] Beryl broke my laptop"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Kasyx on 2008-02-20
In my desperate need to look at pretty things, I decided to install Beryl in the hope that it would sate me. It didn't.

None of the themes would load, my window titlebars are now non-extistent, I can't type into Eterm or the run command, and superkaramba is screwing me around. This is, of course, after I uninstalled Beryl completely.

Help?

---

### Post by Vadi on 2008-02-20
Beryl is very old and unsupported anymore. It's compiz fusion what you're looking for now.

Are you using Gnome or KDE as your desktop enviroment?

---

### Post by Kasyx on 2008-02-20
Oh yeah, I should've mentioned that. I am using KDE. 

I generally use compiz-fusion on my desktop, but I was downloading some Beryl Emerald window decorations which is kinda why I installed this demon in the first place. Any clue why my window title bars are gone and my desktop is all messed up even though I have uninstalled everything?

---

### Post by Kasyx on 2008-02-20
Looks like pretty much anything to do with my desktop isn't working either. Nor is the run command, nor are most buttons... wtf?

---

### Post by Vadi on 2008-02-20
No it just means Beryl crashed. It's a window manager, so it's responsible for some of the graphical stuff, and that isn't functioning.

Unfortunately, I don't know how to get kde's window manager to take over. I know you can do "metacity --replace" or "compiz --replace" in gnome.

---

### Post by Kasyx on 2008-02-21
Solution!

kwin --replace

This will allow the kwin window manager to take over from the broken Beryl.

Thanks for the help :)

---

### Post by Vadi on 2008-02-21
Excellent, and you're welcome.

---

