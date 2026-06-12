---
title: "Brightness and Backlight keys die after waking from suspend"
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-07-01
When my macbook pro(purchased 02/08) wakes from suspend the keys that control the keyboard backlight and monitor brightness simply won't do anything. The little icon pops up when I press the button but the settings don't change. I try restarting pommed but that has no effect. I believe hal and something else now controls keyboard backlight and screen brightness, not pommed.

---

### Post by Rog-Mahal on 2008-07-02
I think some daemons crash during wakeup from suspend... you might want to check your dmesg and system log output to see if that gives you a lead on something. Sorry that this advice isn't very specific.

---

### Post by cvasilak on 2008-07-02
I am having the same problem :(

---

