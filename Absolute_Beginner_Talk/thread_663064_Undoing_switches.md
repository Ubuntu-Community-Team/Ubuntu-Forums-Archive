---
title: "Undoing switches"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by newnet on 2008-01-09
For example: I have "nano -w" aliased.  But sometimes, I need the wrap, how do I undo the switch without editing .bashrc or creating another alias for it?  Using "nano +w" from the prompt would not work.

---

### Post by aktiwers on 2008-01-09
Im not sure what you want to do.. but check:
 ```
man nano
```

Maybe its the nano -r you  are looking for?

But check the man page (command above) and see if I understood you correct.

---

### Post by pjkoczan on 2008-01-09
You can run "unalias nano" (i'm assuming that's the alias) to temporarily remove the alias and then run alias nano="nano -w" when you are finished. Unaliasing something will only remove its alias in that particular shell instance. Other running shells and new shells are unaffected.

Or you can just use the absolute path, /usr/bin/nano. This will bypass the alias (unless you also created an alias named "/usr/bin/nano", but I don't know why you'd do that).

Hope this helps.

---

