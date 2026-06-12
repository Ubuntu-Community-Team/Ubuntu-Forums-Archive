---
title: "trash is not just trash"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Harry789 on 2007-07-25
on my external 80Gb HDU i realize that there are now 3 hidden trash folders:

.500-trash
.root-trash
.laan97ac-trash

I can see deleted files in each of the folders but when I empty my trash on my desktop for example, the files do not all disappear.

How can I wipe them all out?

...and why do they appear?

is it because I mount the drive under different usernames so that permissions are messed up?

---

### Post by vexorian on 2007-07-25
It all in one looks like they are of three different users. If you are not any of those users then this is a file manager bug that should be reported, else try logging in as those users...

---

### Post by Harry789 on 2007-07-25
I just changed from Mandriva 2007.1 to ubuntu. My system likes ubuntu much better.

I did use this 80 Gb drive on Mandriva as well

I have read somewhere else that .500 is setup by Mandriva as standard. I cannot login as 500 obviously so I guess I can safely delete those files.

.root-trash, must be root user login - from mandriva I guess. So I am not sure that just because I run 
$ gksudo nautilus 
that that would allow me to delete that folder?

I will give it a try - user laan97ac is the same user i used on Mandriva 2007.1 and ubuntu so that should be simple enough

thanx!

---

### Post by vexorian on 2007-07-25
yes, running nautilus with sudo should allow you to remove the trash.

---

