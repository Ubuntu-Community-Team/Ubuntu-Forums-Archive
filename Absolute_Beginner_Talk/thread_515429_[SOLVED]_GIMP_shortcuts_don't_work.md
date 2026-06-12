---
title: "[SOLVED] GIMP shortcuts don't work"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-08-02
When using GIMP pen tool, while holding the alt key, it's supposed to move a point.  However, ubuntu move window shortcut kicks in and I end up moving the GIMP window.

Is there a way to temporarily disable this feature?

I want to be able to use all gimp shortcuts w/o problem while I use it.

---

### Post by superbungalow on 2007-08-02
ctrl-alt?

---

### Post by purdticker on 2007-08-04
?

---

### Post by Chris S. on 2007-08-04
At a terminal, run gconf-editor.

Go to apps->metacity->general.  The behavior is probably caused by the "mouse_button_modifier" setting.  You could change it to something that won't conflict with your GIMP shortcuts, or set it to <no value> or disabled (maybe) to turn off this feature.

If you are using Beryl or the new Compiz Fusion then this setting *may* also be mirrored there, and you might have to change it there as well.

---

