---
title: "su pass"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by racebit on 2006-08-06
Hey all, 
   I need some help getting my su pass figured out. I went to kommand and typed su at the runline and entered my default root pass, with no luck.Is there a default root pass for kommand that i don't know about? THanks
-Racebit

---

### Post by geokok1981 on 2006-08-06
I think (without being 100% sure) that the problem is that you trie "su", which does not exist in Ubuntu.
Try "sudo" instead and let me know if that was the problem.

---

### Post by catlett on 2006-08-06
There isn't a root password in ubuntu. Ubuntu uses sudo. You do not log in as root nor do you su to a root terminal. Ubuntu is configured so you become root on a per command basis. Whenever you need to issue a command as root, you preface the command with sudo and then you enter your user pasword.
The first user made at install has sudo powers (actually it is superuser powers. sudo stands for superuser-do) after that any user added does not become a sudoer automatically. He/she is just a user.
Here is the official word [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you really want to use su or you want to be at a root terminal, there are workarounds [http://doc.gwos.org/index.php/DapperGuide#How_to_set.2Fchange.2Fenable_root_user_password](http://doc.gwos.org/index.php/DapperGuide#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by Kurt` on 2006-08-06
Even if you do set a regular root password, do not remove your primary desktop user from the "sudoers" file, as your user needs sudo rights to run Synaptic, change system date/time, and so forth.

---

