---
title: "[SOLVED] adding to app menu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-28
Can someone tell me how to add to the apps menu for program startup

Example        mondoarchives  requires sudo and the password. How would that be included in the startup command for the apps menu.


Thanks

---

### Post by mcduck on 2006-12-28
You can (and should) use gksudo for launching graphical applications. It gives you a popup window asking for your password for sudo.

So the command you need is 'gksudo mondoarchives'. :)

---

