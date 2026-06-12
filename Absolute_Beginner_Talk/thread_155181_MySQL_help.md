---
title: "MySQL help"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by truNWA on 2006-04-04
When setting up mySQL i thought i had doen everything to set it up.

but when i do a test i get the scree below..... I think i need to start apache or something but i have no clue. any suggestions?

---

### Post by nickj6282 on 2006-04-04
Looks like apache is running but not mysql. Try this in the terminal and then see if your connection page works again:

```
/etc/init.d/mysql start
```

Good luck,
-Nick

---

### Post by truNWA on 2006-04-04
[QUOTE=nickj6282]Looks like apache is running but not mysql. Try this in the terminal and then see if your connection page works again:

```
/etc/init.d/mysql start
```

Good luck,
-Nick[/QUOTE]

johnathan@ubuntu:~$ /etc/init.d/mysql start
bash: /etc/init.d/mysql: No such file or directory
johnathan@ubuntu:~$

---

### Post by stalefries on 2006-04-04
Try whereis mysql.

---

### Post by nickj6282 on 2006-04-04
Ok, I figured it out. Installing MySQL just installs the client components. To install mysql server:

```
sudo apt-get install mysql-server
```

That should install and start it. To make sure it always runs, go to "System" --> "Administration" --> "Services" (in Gnome). Then scroll down to the entry for "Database Server (mysql)" and make sure the box is checked.

Good luck!
-Nick

---

### Post by truNWA on 2006-04-05
[QUOTE=nickj6282]Ok, I figured it out. Installing MySQL just installs the client components. To install mysql server:

```
sudo apt-get install mysql-server
```

That should install and start it. To make sure it always runs, go to "System" --> "Administration" --> "Services" (in Gnome). Then scroll down to the entry for "Database Server (mysql)" and make sure the box is checked.

Good luck!
-Nick[/QUOTE]


Thanx nick, i had a power outage last night so my DSL stoped working.

---

