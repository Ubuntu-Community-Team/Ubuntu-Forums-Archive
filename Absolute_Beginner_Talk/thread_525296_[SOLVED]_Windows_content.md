---
title: "[SOLVED] Windows content"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by conphara on 2007-08-14
Using Gnome; how do I make it un-show windows content in normal Metacity decoration?

---

### Post by BaffledMollusc on 2007-08-14
> **conphara said:**
> Using Gnome; how do I make it un-show windows content in normal Metacity decoration?
I can't figure out what you mean. Could you explain a bit more?

---

### Post by conphara on 2007-08-14
Enable transparent content when dragging windows. You know, when you press the left mouse button on the wondow's titlebar and drag it, it show dotted-lines as it's form instead of showing the content in the window while dragging.

Do you know what I mean? :confused:

---

### Post by conphara on 2007-08-15
I found this somewhere in another thread, thanks anyway.

Use gconf-editor (in Terminal, or if you un-hide it using the menu editor, it's the Configuration Editor under Applications --> System Tools),

set “/apps/metacity/general/reduced_resources” to true

---

