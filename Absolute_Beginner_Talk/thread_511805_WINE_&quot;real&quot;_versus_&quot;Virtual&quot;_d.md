---
title: "WINE &quot;real&quot; versus &quot;Virtual&quot; drive problem"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by yeastpuppet on 2007-07-28
How can I either write to the "virtual" C drive in WINE, or how can I get WINE to recognize my real physical drives?

I'm working on getting Mastercook working under wine.  I found a great open source program called Gourmet Recipe Manager, but my version of Mastercook doesn't export files compatible with GRM

Thanks - YP

---

### Post by vexorian on 2007-07-28
/ is converted to Z:\ by wine.

So as long as you got enough priviledges you can use Z:\ to browse your local file system, and eventually get to mounted drives as well.

---

### Post by wolterh on 2008-02-02
Ok, How can I use the libraries on my real drive (C:) and the programs on my second drive (D:) ?
I think the solution would be replacing wine's idea to have a virtual drive, for the location of the real drive..

---

### Post by The Cog on 2008-02-02
Wines virtual dive C isn't all that virtual. it's in your home directory in .wine/drive_c. .wine is hidden (it starts with a dot) so you need ot turn on viewing of hidden files in nautilus by pressing Ctrl-H.

---

