---
title: "Can't add/remove software"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by mkirkelund on 2007-10-24
Hi All.

When i'm trying to add software from the Add/Remove software menu, I simply can't.
If I double click on a program it says: "Click on 'Reload' to load it. To reload the list you need a working internet connection.". I do that, and the exactly same thing happens again if I want to install a program. I've tried to reboot with no succes.
What seems to be the problem??

/Mkirkelun

---

### Post by Paul820 on 2007-10-24
Have you updated the sources list? From the terminal:
> sudo apt-get update
Then try it again.

---

### Post by mkirkelund on 2007-10-24
It didn't work :(.
Any other suggestions? It's because I want to install compizsetting-blabla manager.

---

### Post by Maestro23 on 2007-10-24
Go into Software Sources and make sure all your repos are checked.

System>> Admin>> Software Sources

Try again.

If that doesn't work, post the output of your sources.list file

> cat /etc/apt/sources.list

---

### Post by mkirkelund on 2007-10-24
Briliant! It worked! Thank you!

---

