---
title: "Permissions for Multiple Groups"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by w00ten on 2007-01-09
Hi everyone,

I have a riddle, a conundrum shall we say. What does one do when he/she wants to give different permissions to a folder for different groups. 

Example:
We want group1 and group2 to have 777 access to Folder1, but we do not want group3 and group4 to have any access.

First inclination is an ACL, however, that is not an option. It must be done from the command line.

Any suggestions?

Thanks a bunch,
w00ten

---

### Post by taurus on 2007-01-09
Put group1 & group2 in one group, Group1, while put group3 & group4 in another group, Group2.  Then, change the permission of the directory to Group1 so only group1 & group2 have access to it.  Change the permissions of that directory to 770.

---

### Post by w00ten on 2007-01-09
hmmm... so simple... the answer was basically on the paper too... stupid cold... cant think straight, thanks a bunch.

---

### Post by w00ten on 2007-01-09
ok, question number 2.

Group1 needs rwx, group2 needs rx, 3 and 4 need nothing.  We are back to stumped lol!

---

### Post by taurus on 2007-01-09
In that case, why not make group1 the owner of the directory.  Let group2 belongs to the group of the directory and change the permissions of the directory to 750.

---

### Post by w00ten on 2007-01-09
That thought had crossed my mind, however, I did not think that a group could be a folder owner, I thought that it had to be a user. I'll give it a shot... and no go...

just did chown <groupname> <folder>
and it came back saying invalid user.

---

### Post by hal10000 on 2007-01-09
For such fine-grained permissions i you might use ACL's. But take in mind that not all linux programs suports ACL.

---

### Post by w00ten on 2007-01-10
ACL's are not an option in this case. Which really makes it a pain in the backside. I am really stumped on this one...

---

