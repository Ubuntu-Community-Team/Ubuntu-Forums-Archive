---
title: "need help setting up file server"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-30
how do i figure out my what to put in the last one

in the file that you edit to work with my mysql i feel in the blue spots

$mysql_host="[COLOR="Blue"]your_host_name.com[/COLOR]";
$mysql_username="[COLOR="Blue"]your_username[/COLOR]";
$mysql_password="[COLOR="Blue"]your_password[/COLOR]";
$mysql_database="[COLOR="Blue"]your_database[/COLOR]";

for the last one:
$mysql_database="[COLOR="Blue"]your_database[/COLOR]";

i need to know what to put of the "your_database"
because it's not connecting my my mysql...:(

---

### Post by peitschie on 2008-03-30
For the database, you need to create a mysql database before you can connect it... What program is this setting up?

---

### Post by RadiationHazard on 2008-03-30
eXtreme File Hosting v1.5

---

### Post by peitschie on 2008-03-30
Hmmm... I'm surprised the installation instructions don't cover the creation and setup of the database & relevant users in mysql!

A quick summary of the relevant steps you need to perform:
[LIST=1]
[*]On the database server login to mysql
[*]Create a new database using the command replacing databasename with the name you want (ref: [http://dev.mysql.com/doc/refman/5.0/en/create-database.html](http://dev.mysql.com/doc/refman/5.0/en/create-database.html))```
CREATE DATABASE databasename;
```
[*]Create a new user using the command replacing databasename, username and password with your own values (ref: [http://dev.mysql.com/doc/refman/5.0/en/grant.html](http://dev.mysql.com/doc/refman/5.0/en/grant.html)).  Note, this will ONLY grant access from the local computer (by the @localhost part)! ```
GRANT ALL ON databasename.* TO 'username'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;
```
[*]Test your connection...
[/LIST]

---

