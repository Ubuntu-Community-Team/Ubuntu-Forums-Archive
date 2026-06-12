---
title: "CD-ROM Disc on desktop?"
date: 2006-07-22
forum: Apple PPC Users
---

### Post by Christiaan on 2006-07-22
After installing Unbuntu Dapper on a MacBook under Parallels I have a CD-ROM Disc sitting on my desktop. Does anyone know what this is and how I get rid of it?

---

### Post by Jagot on 2006-07-22
Hit alt+f2 then gtype 'gconf-editor'

Now navigate to apps -> nautilus -> desktop

Untick the box next to 'volumes_visible'

---

### Post by Christiaan on 2006-07-22
Hi Jagot, thanks for the quick response. alt+f2 pops me out of Unbuntu, however, and opens Apple's System Preferences.

---

### Post by Jagot on 2006-07-22
Ok, try and run the command 'gconf-editor' from the Terminal instead.

---

### Post by Christiaan on 2006-07-22
How do I run gonf-editor? What command should I use?

---

### Post by Jagot on 2006-07-22
Sorry - spelling error - missed out the c - in Terminal type gconf-editor

---

### Post by Christiaan on 2006-07-22
Thanks, that did the trick. Pretty complicated for such a simple task though.

---

