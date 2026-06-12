---
title: "A more responsive &quot;hide the panel&quot; option ?"
date: 2009-02-13
forum: Art &amp; Design
---

### Post by JorgeMIlla08 on 2009-02-13
Is there a hack or... anything that could make the "hide the taskbar" more responsive maybe with more than two frames of animation also? by more responsive i mean inmediatly after i hover the mouse over it rises, and not like 4 hours later?

---

### Post by mcduck on 2009-02-13
You can just set the hide & unhide delays with gconf-editor. Start it and browse to apps/panel /toplevels/*yourpanel*.

The default values for both are 500ms, change that to zero and your panel will pop up & hide immediately.

---

### Post by JorgeMIlla08 on 2009-02-21
Thanks !

---

### Post by binbash on 2009-02-21
> **mcduck said:**
> You can just set the hide & unhide delays with gconf-editor. Start it and browse to apps/panel /toplevels/*yourpanel*.

The default values for both are 500ms, change that to zero and your panel will pop up & hide immediately.

Nice trick, thanks

---

