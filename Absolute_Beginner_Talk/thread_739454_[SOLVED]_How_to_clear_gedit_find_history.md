---
title: "[SOLVED] How to clear gedit find history?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2008-03-29
How do you clear gedit's find history?  I purged / reinstalled gedit but that didn't help.

---

### Post by Daveth on 2008-03-29
I think this is what you are after

[http://ubuntuforums.org/showthread.php?t=212482](http://ubuntuforums.org/showthread.php?t=212482)

---

### Post by saj0577 on 2008-03-29
He means the program gedit which is slightly different mate.

Saj

---

### Post by y-lee on 2008-03-29
Open the configuration editor by typing the following into the terminal (or finding it in your menu :) )

```
gconf-editor
```

go to **apps --> gnome-settings -->gedit**. In the right panel you should see 2 entries, **history_gedit2_replace_with_entry** and **history_gedit2_search_for_entry**. Right click either one of these and pick edit key. Now delete away.

Good question btw, i had to look around my machine to figure it out and google wasn't much help :lolflag:

---

