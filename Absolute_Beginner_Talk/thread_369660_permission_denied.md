---
title: "permission denied"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by pdxcurry on 2007-02-24
I am trying to run a script and I cannot not seem to get the correct permission to do so.  The script is in /usr/local my code is

# scripts/mysql_install_db.sh --user=mysql

the error I get is 

-bash: scripts/mysql_install_db.sh: Permission denied

The script came on a cd with a book on learning PHP, MySQL and Apache.

---

### Post by taurus on 2007-02-24
Try to run it with the **sudo** in front of the command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pdxcurry on 2007-02-24
OK I tried that and it look liked this

root@freekbox:/usr/local/sql# sudo /scripts/mysql_install_db.sh --user=mysql
sudo: /scripts/mysql_install_db.sh: command not found

also tried this

root@freekbox:/usr/local/sql# sudo scripts/mysql_install_db.sh --user=mysql
sudo: scripts/mysql_install_db.sh: command not found

---

### Post by taurus on 2007-02-24
Post the output of the last command here.

```
cd /usr/local/sql/scripts
ls -la mysql_install_db.sh
```

p.s.  I see that you are logged in as root so you better be careful or one wrong command can crash your machine.

---

### Post by pdxcurry on 2007-02-24
-rw-r--r-- 1 503 users 8701 2006-05-25 01:56 mysql_install_db.sh

ps thanks changed from root

---

