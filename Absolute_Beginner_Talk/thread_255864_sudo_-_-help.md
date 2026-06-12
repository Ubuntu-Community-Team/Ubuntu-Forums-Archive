---
title: "sudo - -help"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by arsadogi on 2006-09-12
i have read sudo manuals and i anderstood that sudo is a command to immpliment root commands because in dapper drake root account is hibernated.the problem is when i type in Terminal[COLOR="Red"]sudo chown username /something[/COLOR]i get the message [COLOR="red"]you are not permmited...[/COLOR]please give me  an explanasion.:roll:

---

### Post by anaconda on 2006-09-12
You should be able to chown using sudo.

But some things cant be made using sudo.. like editing sudoers list.

In those rare? cases it is better to actually become root using:
sudo su
and then doing whatever needs to be done.
typing exit takes you back to normal user rights..

---

### Post by arsadogi on 2006-09-12
but i use chown directories like mounting points.for example say i mount mt fat32 windows partition in the directory /home/username/1
the owner of this folder is root.with sudo chown a can't set the owner of /home/username/1 username.

---

