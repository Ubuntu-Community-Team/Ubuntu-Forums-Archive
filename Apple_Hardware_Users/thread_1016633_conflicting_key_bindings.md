---
title: "conflicting key bindings"
date: 2008-12-20
forum: Apple Hardware Users
---

### Post by freakalad on 2008-12-20
Having trouble with my key-bindings/shortcuts.

Trying to do stuff like adjust keyboard backlight with <fn> F8, F9 & F10, but this launches Evolution & RhythmBox instead.

MBP SantaRosa, Intrepid.

I suspect I may have multiple apps bound to overlapping keyboard shortcuts (most likely not). Unable to locate where these may be originating. Eliminated Compiz as a culprit.

Since pommed has been deprecated, I'm not too sure that the backlight is actually functioning.

Where can I reset some of these settings to a default?

---

### Post by Rog-Mahal on 2008-12-20
I think by default pommed maps things like keyboard backlight and screen brightness to just the key, and you get the "f9" function by pressing fn + key. You can reverse this behavior by editting your /etc/pommed.conf. Switch the "fnmode = 1" to "fnmode = 2" And that should work. There are also some other variables for things like backlight functionality, but I didn't look to closely. Hope that's a start.

---

### Post by freakalad on 2008-12-21
Thanks for the info

I think pommed has been deprecated by the use of applesmc (which gets updated more frequently)

I can still install pommed, but this causes some issues, and would still not address the issue of other applications bound to certain keys

---

