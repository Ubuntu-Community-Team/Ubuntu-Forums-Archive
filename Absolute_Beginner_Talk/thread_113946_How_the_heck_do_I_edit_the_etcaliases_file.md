---
title: "How the heck do I edit the /etc/aliases file?"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by racin on 2006-01-07
Hi  All,
New convert, tried Lindows in the early days and ended up not liking it. I have Ubuntu loaded on two computers. The desktop with wired lan is working great! I'm following the wireless troubleshooting guide for my Pentium 4 Gateway laptop. I have progressed through the guide to the point where I need to edit three lines in the /etc/aliases file but I have run into a snag. The file is owned by root and it is read only. I'm sure someone can help me edit this file. It's probably easy but I'm still a linux newb!:o  Thanks in advance for all the help. Take Care

---

### Post by bored2k on 2006-01-07
Try this code (from a terminal):
```
sudo gedit /etc/aliases
```You will be asked for your password. After putting it correctly, a new editor should load.

Note: if you are on KDE, replace gedit for kwrite (or kdesu kwrite instead of sudo).

---

### Post by racin on 2006-01-07
OK I did that and a new terminal window opened but now there is just a tabbed page titled Aliases that says # Added by installer for initial user root: <user name>

---

### Post by bored2k on 2006-01-07
That is your aliases file.

---

### Post by racin on 2006-01-07
hmmm that is wierd I expected to see alot more information??
Oh thanks for the help I appreciate it!

---

### Post by racin on 2006-01-07
Ahhh I need to edit the /etc/modprobe.d/aliases file...Ahhhh I had a late night working on this.. I guess I should have went back and reread it thanks again for the help!

---

