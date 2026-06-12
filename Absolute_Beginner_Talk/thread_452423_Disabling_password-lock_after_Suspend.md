---
title: "Disabling password-lock after Suspend?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by ThinkBuntu on 2007-05-23
This is certainly a beginner's question, but a lazy forum search didn't find the answer.

How do I disable screen-locking when I close my laptop lid (which suspends to ram)? It's a pain to type in my password every time. I'm the only user, so no security concerns.

---

### Post by ThinkBuntu on 2007-05-23
Pretty please...?

---

### Post by cymen on 2007-05-23
So I had a quick search to confirm some vague suspicions (I don't use Gnome) and here's what apparently should do the trick:

```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_suspend false
```

Some other options I saw might also be of interest. They're all pretty self explanatory:

lock_on_blank_screen
lock_on_hibernate
lock_on_use_screensaver_settings

---

### Post by ThinkBuntu on 2007-05-23
When in doubt, check out gconf-editor...how could I forget?

---

### Post by est on 2007-05-31
Thanks! It was annoying me I couldn't control music playing on my laptop with the remote if the lid was closed. The related "lock_on_blank_screen" fixed that.

---

