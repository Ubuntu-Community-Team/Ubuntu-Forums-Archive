---
title: "no access to administratio tools after renaming user"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rmax on 2007-10-20
Hi, I've unfortunately renamed my user name with the system-administration-user/groups tool and after rebooting I cannot access most of the administration tools anymore. Seems that I lost all my privileges ](*,) and I also have no clue what the original root password was. Anyone out there who has an idea how this can be fixed? Am desperate...

---

### Post by chalex on 2007-10-20
What you want to do is edit the files /etc/passwd and /etc/group to have the appropriate user in the appropriate group.  That's what the GUI tool does for you, but it sounds like it didn't do something correctly.

Edit the file /etc/group and replace every occurence of your old username with your new username.  You can edit the file either by booting off the LiveCD and mouting your hard drive or by rebooting into single-user mode.

---

### Post by steve.horsley on 2007-10-20
Of course, you wil have to boot into recovery mode to do that (this gives you a root text prompt). You need to ensure that your user is a member of the group admin. You can do this (as root) with the command 
**adduser rmax admin**
or whatever your new name is.

---

### Post by rmax on 2007-10-20
thanks steve, that worked perfectly! I so enjoy the switch to Ubuntu, it brings back all those embarrassing newbie moments I had 10 years ago with windows... Ah, glory days!

---

