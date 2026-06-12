---
title: "permissions not being changed to what I requested"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by timsch75 on 2005-12-30
I have a partition that I am mounting in fat32 format.  It mounts fine, but I am stuck with the default permissions:

drwxr-xr-x   4 root root 16384 2005-12-30 19:43 media/w2

I've sudo chown 777 'ed, no error message is returned, but the permissions remain the same.  Why is this?  This limited root user business is starting to smell a little bit too windozish for my liking....

---

### Post by lleb on 2005-12-30
[QUOTE=timsch75]I have a partition that I am mounting in fat32 format.  It mounts fine, but I am stuck with the default permissions:

drwxr-xr-x   4 root root 16384 2005-12-30 19:43 media/w2

I've sudo chown 777 'ed, no error message is returned, but the permissions remain the same.  Why is this?  This limited root user business is starting to smell a little bit too windozish for my liking....[/QUOTE]

that would be because chown is for chaning the owner, not the permissions.  to change the permissions you would need to chmod 777 media/w2  that will change things to all rwx as you are looking for.

---

### Post by kaamos on 2005-12-30
You should change the defaut mounting parameters. Look here [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by timsch75 on 2005-12-30
[QUOTE=lleb]that would be because chown is for chaning the owner, not the permissions.  to change the permissions you would need to chmod 777 media/w2  that will change things to all rwx as you are looking for.[/QUOTE]

My mistake.  I meant that I had tried chmod 777.....  After trying that I had tried to change ownership, also with no success

Edit:  Thanks kaamos.  changing fstab did the trick.  I had it setup like I was used to in Slackware.  I don't know why there would be a difference in terminology between the distros.

---

### Post by lleb on 2005-12-31
kewl, glad that worked.  fstab is still tricky stuff for me.

---

