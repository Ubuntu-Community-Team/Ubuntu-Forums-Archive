---
title: "save a gnome workspace?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by jimmy the saint on 2008-02-18
I know I can save the current workspace to be restored the next time you sign in.  I am looking for a way to save the current workspace and be able to use it at any time.  In other words, say I have three applications open in a specific layout and it is working for a task that I do frequently, I could save it as "task 1 workspace" and at any time call it up.

---

### Post by paultag on 2008-02-18
not sure if this is what you want:
System --> Prefs --> Sessions
Under Session Options, I think you can save your sessions. Give it a shot.

If you are talking about being able to launch a few apps at a time, look into Bash scripting. You can make a quck script that pulls up more then one app like this:

```

#!/bin/bash
  firefox &
  pidgin &

```

Cheers,
Tag

---

