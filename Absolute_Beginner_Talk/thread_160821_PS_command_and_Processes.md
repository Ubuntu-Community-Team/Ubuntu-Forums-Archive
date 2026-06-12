---
title: "PS command and Processes"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by utab on 2006-04-15
Dear all,

When I open skype, amarok, CD player all together for example and then open up a terminal window and type ps command I only get
 
PID TTY          TIME CMD
 8931 pts/0    00:00:00 bash
 9296 pts/0    00:00:00 ps

I can not get messages about the programs running and their ids. If I want to kill command, how will I be able to use since I can not see the pid values.

Thx.

---

### Post by trent dillman on 2006-04-15
ps -u <your user name>

or

ps -e (everyone)

or

ps -fAH (everyone, tree view)

---

### Post by utab on 2006-04-15
THX for the quick reply.

---

