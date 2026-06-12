---
title: "Evolution Settings Restore Problem"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by aridus on 2008-04-02
I have moved to a new computer and fresh instatllation of 7.10 and want to restore my evolution settings and e-mail using the file-restore settings in evolution. I have done this before and it works well. However, this time when I choose the backup file the process starts, aborts shortly afterwards, and tries to start again. Help - does anybody know what is going on and how I may restore my settings? thanks! Martin

---

### Post by ChronoSphere on 2008-04-02
I don't know what the problem could be, but you could do it manually:

zip -r evo-bak.zip .evolution .gconf/apps/evolution/mail .gnome2_private/Evolution 

Then on the fresh installation:

unzip evo-bak.zip -d ~

---

### Post by aridus on 2008-04-02
many thanks for that - and I will try it out! Martin

---

