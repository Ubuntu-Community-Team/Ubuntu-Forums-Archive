---
title: "[SOLVED] find a directory?"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by stainless_steel on 2008-04-05
how the heck to i do a search for a directory rather than a file?

---

### Post by riven0 on 2008-04-05
I'm not an expert at bash, but you can try: **find -name whatever** in the terminal.

---

### Post by stainless_steel on 2008-04-05
tried it:

"find: ./.gnome2/gnome-btdownload: Permission denied"

i dunno what thats about

---

### Post by riven0 on 2008-04-05
Hmm, try something like this:** find -type d | grep whatever-your-searching-for**

---

### Post by superprash2003 on 2008-04-05
go to Places=>Search for files and search.. it will also give you search results for directories

---

### Post by stainless_steel on 2008-04-05
so it does. (duh) 
i knew there was a simple solution

---

