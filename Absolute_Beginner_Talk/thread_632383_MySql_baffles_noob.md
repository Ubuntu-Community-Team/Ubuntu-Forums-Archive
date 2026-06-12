---
title: "MySql baffles noob"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-12-05
'Spent hours on the mysql site, install intructions, and several questions seem unanswered. These are painfully basic:
1) can mysql run as a stand-alone database app, or does it REQUIRE a running web server (apache or other)?

2) No ubuntu packaged binaries exist, but the Debian Apt-get seems fine. Once downloaded, none of the instructions from mysql site works, beginning w/ changing root password. Has anyone done the install on an ubuntu box that could point to a good place to read for a noob to get it going?
 
3) One weakness that appears w/ mysql compared to Sql Server, is the lack of gui. It looks like there's at least one or two out there. Has anyone worked with them? Recommend them?

---

### Post by The Cog on 2007-12-05
MySQL is a database server. It runs as a server, in the background with no visible GUI. No web server is required (although you may want a web server to serve pages to your users, based on contents retrieved from the database server). Since MySQL (the server) has no GUI, you need some kind of way to view and enter data into the database. A web server (with supporting scripts) is one way, but you generally have to write special code for the web server that displays the data in the way you want, and specially designed forms for data input. MySQL comes with a command-line client for creating tables and contents - this takes SQL commands such as CREATE TABLE... and SELECT..., but this should not be confused with the MySQL database server - client and server are as separate as a browser and a web server are. There are also GUI clients available.

2) Ubuntu binaries do exist. Search for mysql in Synaptic. I suggest you install these packages:
mysql-client
mysql-server
mysql-admin
mysql-query-browser
mysql-navigator

3) Lack of GUI??? What?
See 2) above. I haven't tried mysql-navigator personally, but use mysql-admin and mysql-query-browser frequently. The main problem is finding the time to try all the different GUIs available and decide which you like most. I also sometimes use OpenOffice.org as a GUI for MySQL.

---

### Post by OffAxis on 2007-12-05
phpmyadmin is also a very popular gui for administering mysql.
```
sudo apt-get install phpmyadmin
```

which will also install apache2 and php (web server and web server scripting language).

Like The Cog pointed out, mysql is a standalone database program, so no, a web server isn't necessary (neither is a GUI, either) but it does make things easier.

---

### Post by RH9R on 2007-12-05
Cog & OffAxis, Thank You both. 
My frame of reference has been learning sql 2000 to look at table contents for problems at work or to validate logic for a spec. 
I must say, I'm impressed w/ sql server, but want to avoid the dark side.
 
I have something now to work on t his wkend. I very much appreciate your help.

---

