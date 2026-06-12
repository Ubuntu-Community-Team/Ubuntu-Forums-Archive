---
title: "users and groups"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-02-24
What do I have to do to get to the system admin users and groups? I use my logon  
password, but it says I do not have permission.

bob

---

### Post by al1b1 on 2007-02-24
try typing in root or leaving it blank

---

### Post by bapoumba on 2007-02-24
> **bratliff said:**
> What do I have to do to get to the system admin users and groups? I use my logon  
password, but it says I do not have permission.

bob
Are you logged using the first user created when installing Ubuntu?
What does return **groups** in a terminal (> Accessories > Terminal) ?

---

### Post by bratliff on 2007-02-24
Yes I am logging is as the first user. 

bob@bob-desktop:~$ return **groups** in a terminal (> Accessories > Terminal) ?[/QUOTE]
bash: syntax error near unexpected token `('
bob@bob-desktop:~$ return **groups**                                        
bash: return: **groups**: numeric argument required
bash: return: can only `return' from a function or sourced script
bob@bob-desktop:~$ return  B groups /B
bash: return: B: numeric argument required
bash: return: can only `return' from a function or sourced script
bob@bob-desktop:~$ 




[QUOTE=bapoumba;2204029]Are you logged using the first user created when installing Ubuntu?
What does

---

### Post by nhandler on 2007-02-24
Just enter the one word *groups* in a terminal

---

### Post by bratliff on 2007-02-25
bob@bobinpanama:~$ groups
bob adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
bob@bobinpanama:~$ 

To resolve the problem, I reinstalled Ubuntu 6.10. But thanks for the help. 

Robert

---

