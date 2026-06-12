---
title: "To where should I back up my network files?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by adamonline on 2007-01-14
Hi all,

I want to use this computer, running Ubuntu 6.06, to store some back up files on from my Windows XP computer.

I have Samba set up already.

By linux standards, what would be the ideal directory to keep these files?

Also, when I'm on my Windows machine and access my linux computer through the network, it asks me for my username and password.  Would it make sense to create a new user named 'share', and just use /home/share to back the files up on?

Any thoughts or input would be much appreciated :)

-ADAM

---

### Post by blackened on 2007-01-15
Really this is just a matter of personal preference. I myself would just create a backup directory under your standard login home directory a la:
/home/*myusername*/backups

There's no real right or wrong way, whatever is easiest for you.

---

### Post by adamonline on 2007-01-15
Cool, thank you!

-ADAM

---

