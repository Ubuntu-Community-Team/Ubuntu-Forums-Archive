---
title: "CTRL-ALT-Fkeys dont work."
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Kitsun on 2007-09-25
The CTRL-ALT-Fkeys don't get me into the terminal anymore, they had previously worked.

I really want these to work again, because its the only way I can recover from the laptop lid being closed without restarting X (ctrl-alt-backspace).

Thnx

---

### Post by wolfen69 on 2007-09-25
some keyboards require you to activate the F keys by pressing a button on the keyboard. look around a little.

---

### Post by Dr Small on 2007-09-25
You may have to turn F LOCK on, as what wolfen69 was saying.

---

### Post by Kitsun on 2007-09-27
My keyboard does not have a F-Lock key, and the hotkeys using the F-keys work (Like ALT-F2).

---

### Post by capink on 2007-09-27
Try the following command:

```
sudo chvt 2
```

If the above command works, you can map it to whatever key combination you want. But you will need to add the command chvt to sudoers in order for this to work.

---

### Post by Dr Small on 2007-09-27
Haha! That is the command I have been looking for, so I can change virtual terminals without using the keyboard shortcuts!

Thanks Man :D

Dr Small

---

