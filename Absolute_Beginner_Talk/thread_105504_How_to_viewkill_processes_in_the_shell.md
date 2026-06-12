---
title: "How to view/kill processes in the shell?"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by pedrotuga on 2005-12-18
thats it....

what are the commands for task managing?

thxz

---

### Post by amohanty on 2005-12-18
for all processes by all users:
ps aux

to kill one:
kill -9 <pid, obtained from the previous commnad>

to kill all by name
killall <name>

HTH

---

### Post by pedrotuga on 2005-12-18
cool ;) 
thx there ;)

---

### Post by deNoobius on 2005-12-18
I believe it's as follows:  to see the processes--"top."
To kill--"killall [name of process]"

Also, "sudo xkill" lets you kill a process by clicking on its open window in Gnome.

---

