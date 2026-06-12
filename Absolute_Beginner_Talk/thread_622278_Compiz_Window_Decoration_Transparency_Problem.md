---
title: "Compiz Window Decoration Transparency Problem"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by gubemton on 2007-11-24
For some reason, my window decorations and shadows have this odd transparency, which looks like the desktop background.  I've tried changing the decorations, but I still end up with the same type of effect.  Is there any way to fix this?  If it helps, I'm using the Ubuntu Human Emerald Theme ([http://www.gnome-look.org/content/show.php/Ubuntu+Human+Emerald+Theme?content=69935](http://www.gnome-look.org/content/show.php/Ubuntu+Human+Emerald+Theme?content=69935)).

Thanks in advance!

**EDIT: Solution: Disable reflections plugin.**

---

### Post by gubemton on 2007-11-24
Oh yes.  The attachment is of Nautilus, with the main section removed because it isn't relevant.  The funky grey glass thing is what I'm talking about.  Does anyone have the slightest clue on how this can be fixed?

---

### Post by rax_m on 2007-11-24
Have you tried using compiz settings manager to change the opacity values for your windows?

---

### Post by gubemton on 2007-11-24
In my Compiz opacity settings, there is only a rule for Tilda, which shouldn't affect anything else.  Also, the rest of the window is opaque.  Only the top and bottom fade to transparent with the background.

---

### Post by Billy_McBong on 2007-11-24
i think that theme is supposed to be transparent
you should be able to change it in emerald theme manager

---

### Post by gubemton on 2007-11-24
I don't think so, because in the screenshot, it shows just a shadow.  Also, another thing to note, is that this problem appears on context menus and tooltip shadows too.

---

### Post by gubemton on 2007-11-24
Is there a setting in Compiz that lets you change the tooltip/context menu shadows?  Maybe that'll get me somewhere.

---

### Post by gubemton on 2007-11-24
Oh come on.  Nobody has the slightest idea how to fix this?

---

### Post by hps on 2007-11-24
I have the same problem but managed to get rid of the glow, however the transparency problem is there and as a matter of fact as I log out the whole screen shows that pattern of background but in grey and white.  I am also following this thread with intrest.

---

### Post by gubemton on 2007-11-24
After testing tons and tons of settings, I found out why this happens.

Turns out, it's the reflections plugin.  I don't know why anyone would want that, but somehow, it was enabled, and seemed to be the cause of the problem.

---

### Post by enjay on 2007-12-09
At last! Thanks gubemton!

---

### Post by discoade on 2007-12-09
It was enabled as part of a theme in emerald! just un check reflections in compiz/ effects  Basically you enabled it when you picked the theme!

---

