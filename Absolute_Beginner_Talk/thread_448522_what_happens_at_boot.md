---
title: "what happens at boot?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-19
Is there some way to see a log of what happens at boot, behind the splash screens?

---

### Post by Najand on 2007-05-19
Hmm, you can edit boot command during boot by pushing e when selecting ubuntu in the menu.... Remove "quiet" and "splash" and push enter....

---

### Post by Austin_KW on 2007-05-19
You can edit your boot line from the  grub menu at startup, press 'e' and edit the line to remove 'quiet', you can also remove the 'splash' if you want to see all the text.

You could  edit /boot/grub/menu.lst to remove the quiet.

Or you can just switch to the virtual terminals during boot. ctrl-alt-F1 (to F6) I think most of the boot outputs to terminal1.

---

### Post by kh4nh on 2007-05-19
Another way is:
```
cat /var/log/messages
```

---

