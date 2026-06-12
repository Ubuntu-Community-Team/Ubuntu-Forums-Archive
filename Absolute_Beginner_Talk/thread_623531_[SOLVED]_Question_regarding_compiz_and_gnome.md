---
title: "[SOLVED] Question regarding compiz and gnome"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by juniah on 2007-11-26
I was running compiz, but wine doesn't like it.  So I type in...

metacity --replace

then I get this a bunch of times

Window manager warning: Log level 8: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed


And when I close the terminal the desktop resets itself.

So how do I get gnome to run again?

---

### Post by Majorix on 2007-11-26
Try adding a & after metacity --replace:
```
metacity --replace &
```

That way the desktop won't go back to compiz when you close the terminal.

---

### Post by PeterJS on 2007-11-26
Does metacity actually load? If so I'd ignore the GTK warnings, it likes to scream bloody murder about anything and everything for no particular reason.

You want to run metacity in the background, try:
```

metacity --replace &

```

If that works, give it a moment to get over it's loading fit, hit enter in the terminal, and type exit at the prompt.

---

### Post by juniah on 2007-11-26
See the thing is that in the terminal it never returns the prompt to me.

Im so confused.

---

### Post by juniah on 2007-11-26
I'm trying the & thing now

---

### Post by FuturePilot on 2007-11-26
You could try running it from Alt+F2.

---

### Post by juniah on 2007-11-26
I just did it from terminal using

metacity --replace &

and it gave me back terminal control and erm I think its worked.  How do I test to make sure that it really is working?

---

### Post by PeterJS on 2007-11-26
Does it look and behave like it should? Then it's working.

pragmatism++

---

### Post by juniah on 2007-11-26
Yeah for the most part.  Ok Im marking this as solved until I break it again.

---

