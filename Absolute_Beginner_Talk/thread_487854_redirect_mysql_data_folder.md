---
title: "redirect mysql data folder"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Andra on 2007-06-29
hello

Default mysql data folder is /var/lib/mysql. When I changed this path in /etc/mysql/my.conf parameter datadir, mysql server stopped and couldnt be started.
Should I copy all contents of /var/lib/mysql (debian-5.0.flag, ibdata1, mysql_upgrade_info, mysql folder with .myd, myi, .frm files) to my directory, or what way the task should be accomplished?

---

### Post by letkemanp on 2007-06-30
MySQL using the "mysql" database to store all the MySQL account information. You may not have to move the files from place to place, just create a symbolic link using either Nautilus or from a terminal window using ln. Type 'ln --help' for more infomration on the ln command

---

### Post by Andra on 2007-07-02
Symbolic link - where?
What I would like to do is - on a separate partition put all apache data and all mysql data.  Well, maybe not all data but those related to the task the server is mainly dedicated (run webserver and, using it, collect data in database).
Thank you for reply!

---

### Post by Andra on 2007-07-05
First tried to put a symbolic link in /var/lib/mysql and point it to my directory. It worked. What I didnt like - I created the database in default datadir, cut and copy to my directory, make a link.
Second I followed instructions in
[http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html](http://www.debianadmin.com/mysql-database-server-installation-and-configuration-in-ubuntu.html)
It also worked. But I'm afraid I'm not going to use and test it thoroughly now.

---

### Post by wolfear on 2007-08-27
A bit late, but I was browsing and ran across your post:
You probably already figured this out but I'll post anyway.

If you want your data in a separate partition, find one of the tutorials for moving your home directory to it's own partion and follow that but using your data directory (did that make sense?).

Psycocats has a good one,but I don't have the link handy.

That's how I moved all my web stuff (/www and /var/lib/mysql and a few others). Once the new partition is mounted, no need for symlinks or configuration changes.

Added bonus is not losing everything if (when) the server goes boom.

---

