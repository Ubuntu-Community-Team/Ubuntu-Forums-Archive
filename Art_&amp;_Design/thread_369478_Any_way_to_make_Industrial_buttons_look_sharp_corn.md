---
title: "Any way to make Industrial buttons look sharp cornered and flat like Murrine's?"
date: 2007-02-24
forum: Art &amp; Design
---

### Post by Bastanteroma on 2007-02-24
Industrial gtk theme is my fave, and on the switch from Dapper to Edgy the panel and scrollbars got sharper cornered in a way I liked.  Is it possible to edit a file to give the buttons sharp corners too, like the Murrine ones perhaps?

Probably not that simple, but it would be wonderful.

---

### Post by StarLog on 2007-02-24
Where do the theme files load to, when I try to select one from the System>Themes>window.
It wants me to load a file. How do we change to the shown themes. or am I just dumb on this one.?

Thanks

---

### Post by K.Mandla on 2007-02-25
> **Bastanteroma said:**
> Industrial gtk theme is my fave, and on the switch from Dapper to Edgy the panel and scrollbars got sharper cornered in a way I liked.  Is it possible to edit a file to give the buttons sharp corners too, like the Murrine ones perhaps?

Probably not that simple, but it would be wonderful.
You might check in /usr/share/themes for the Industrial theme, and copy it to ~/.themes and rename it so it doesn't conflict with the default system theme. From there you could hand-edit the gtkrc file to use the engine or colors you like. (In other words, set it to use the Murrine engine and keep the Industrial colors.)

I think the shape of the buttons is determined by the engine, though. So if you want to change the shape of the buttons, you might have to build your engine. That's about all the help I can offer. :roll:

---

### Post by Bastanteroma on 2007-02-25
Sorry, I'm not sure I understand your question, or why you asked it in this thread.

---

