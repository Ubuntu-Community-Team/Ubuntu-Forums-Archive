---
title: "edit files on ssh location in gui / nautilus"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by byenary on 2008-04-11
Hello,

I edit a lot of php pages wich are accesible trough ssh.
Some modification are simple so i do not want to edit the file localy, i want to just open it edit and save/close it.
When I browse to ssh location using nautilus ctrl+l and then do someting like ssh://root@machine...
Then i select the file richt click it and open it with gedit -> it opens it and everything is as I want.
But since gedit is kinda limited editor i want to use an other editor like for example geany, but with all other editor but geany the previous described method wil not open the file.... ??
Any idea why this is ?

Thx

---

### Post by byenary on 2008-04-11
I can only make this work when making the ssh location a smb location and than mount it on the local file system...

---

### Post by Oldsoldier2003 on 2008-04-11
> **byenary said:**
> Hello,

I edit a lot of php pages wich are accesible trough ssh.
Some modification are simple so i do not want to edit the file localy, i want to just open it edit and save/close it.
When I browse to ssh location using nautilus ctrl+l and then do someting like ssh://root@machine...
Then i select the file richt click it and open it with gedit -> it opens it and everything is as I want.
But since gedit is kinda limited editor i want to use an other editor like for example geany, but with all other editor but geany the previous described method wil not open the file.... ??
Any idea why this is ?

Thx

because when you are in a ssh session you are running on that machine inside your terminal session. in order for geany to work it would have to be installed on that machine and forwarded to your machine over the ssh session. for simple edits why not just ssh in and use nano or vi or even emacs?

---

### Post by byenary on 2008-04-11
Yeah,

For the simple edits I do use nano or gedit, but while editing php and chunks of code some advaced editing features can speed up the things a lot...

E.

---

### Post by hyper_ch on 2008-04-11
mount the remote filesystem in your local filesystem with SSHFS.. then you can locally browse through all that.

---

