---
title: "How do I stop X?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2006-02-01
I want to install the nvidia driver for my video card, but I cannot do this while X is running.  I have accidentally booted myself before :rolleyes: but...

Thx in advance for what will surely be a three word answer to an elementary question.  -pete

---

### Post by Lord Illidan on 2006-02-01
```
sudo /etc/init.d/gdm stop
```
should do the trick.

---

### Post by MartinG on 2006-02-01
[QUOTE=TeeAhr1]I want to install the nvidia driver for my video card, but I cannot do this while X is running.  I have accidentally booted myself before :rolleyes: but...

Thx in advance for what will surely be a three word answer to an elementary question.  -pete[/QUOTE]Ctrl+Alt+Backspace kills X, but it restarts itself to the login screen.  Don't worry about that; either do Ctrl+Alt+F1 to a terminal and ignore the login, or login to a terminal from the login screen.  Then do your installation stuff, and either switch back (Ctrl+Alt+F7) or type exit, depending on the route you chose, then do the Ctrl+Alt+Backspace again and X *should* relaunch with your new driver.  

Another way again is to do Ctrl+Alt+F1 to a terminal, and then use top to find and kill X -- that involves exploring top, though.

---

