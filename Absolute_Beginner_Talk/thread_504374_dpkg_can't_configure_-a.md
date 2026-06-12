---
title: "dpkg can't configure -a"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by nairod on 2007-07-19
Hi, 

While installing Mysql (lamp actually) I got an error (seen below)) and the terminal was stuck with that message so after a while I closed it. Since then whenever I try to run the synaptic manager or install anything through the terminal I get

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

After trying both the configure -a and sudo apt-get remove --purge apache2
sudo rm -Rv /etc/apache2/ I get:

Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

and I'm stuck. What do I do now?

---

### Post by KIAaze on 2007-07-19
I'm currently having a pretty similar problem with DansGuardian, but haven't solved it yet.

The simplest solution would probably be to remove mysql-server-5.0 completely and then try to reinstall, but I suppose that won't work with just sudo apt-get remove.
If it does, great, if not:

Have you looked at README.Debian.gz?:
```
sudo gunzip /usr/share/doc/mysql-server-5.0/README.Debian.gz
less /usr/share/doc/mysql-server-5.0/README.Debian.gz
```

It states the following:
> * MYSQL WON'T START OR STOP?
============================
You may never ever delete the special mysql user "debian-sys-maint". This
user together with the credentials in /etc/mysql/debian.cnf are used by the
init scripts to stop the server as they would require knowledge of the mysql
root users password else.
So in most of the times you can fix the situation by making sure that the
debian.cnf file contains the right password, e.g. by setting a new one
(remember to do a "flush privileges" then).


So as a first test, I'd suggest checking if you have that debian-sys-maint user. To list the users on your system, you can use:
```
cat /etc/passwd | cut -d":" -f1
```

It's possible that the removal of apache2 also removed that user.

Another solution I suggest is to manually create the missing "/etc/mysql/debian-start" script. Here's what it looks like:
```
#!/bin/bash
#
# This script is executed by "/etc/init.d/mysql" on every (re)start.
# 
# Changes to this file will be preserved when updating the Debian package.
#

source /usr/share/mysql/debian-start.inc.sh

MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"
MYUPGRADE="/usr/bin/mysql_upgrade --defaults-extra-file=/etc/mysql/debian.cnf"
MYCHECK="/usr/bin/mysqlcheck --defaults-file=/etc/mysql/debian.cnf"
MYCHECK_SUBJECT="WARNING: mysqlcheck has found corrupt tables"
MYCHECK_PARAMS="--all-databases --fast --silent"
MYCHECK_RCPT="root"

# The following commands should be run when the server is up but in background
# where they do not block the server start and in one shell instance so that
# they run sequentially. They are supposed not to echo anything to stdout.
# If you want to disable the check for crashed tables comment
# "check_for_crashed_tables" out.  
# (There may be no output to stdout inside the background process!)
echo "Checking for corrupt, not cleanly closed and upgrade needing tables."
(
  upgrade_system_tables_if_necessary;
  check_for_crashed_tables;
) >&2 &

exit 0

```

=====================================
If it still doesn't work and if you know a little bit how shellscripts work, you might want to look at the shellscripts used during the installation process themselves:
1)Download the mysql-server-5.0 package from [http://packages.ubuntu.com/feisty/misc/mysql-server-5.0]("http://packages.ubuntu.com/feisty/misc/mysql-server-5.0")
2)
```
cd <download dirctory>
mkdir mysql
dpkg --control mysql-server-5.0_5.0.38-0ubuntu1_i386.deb mysql
dpkg -x mysql-server-5.0_5.0.38-0ubuntu1_i386.deb mysql
cd mysql

```
Now you should have all the prerm, postrm, preinst, postinst scripts in the mysql directory, as well as all the other scripts installed with the package.

By the way, that's how I got the "/etc/mysql/debian-start" script above. ;)

edit:
Another potentially interesting part of the README.Debian:
> * PASSWORDS:
============
It is strongly recommended to set a password for the mysql root user (which
is NOT the same as the "normal" root user) with the command:
 /usr/bin/mysqladmin -u root password 'enter-your-good-new-password-here'
If you already had a password set add " -p " before "-u" to the line above.

If you are tired to type the password in every time or want to automate your
scripts you can store it in the file $HOME/.my.cnf. It should be chmod 0600
(-rw------- username username .my.cnf) to ensure that nobody else can read
it.  Every other configuration parameter can be stored there, too. You will
find an example below and more information in the MySQL manual in
/usr/share/doc/mysql-doc or [www.mysql.com](www.mysql.com).

ATTENTION: It is necessary, that a .my.cnf from root always contains a "user"
line wherever there is a "password" line, else, the Debian maintenance
scripts, that use /etc/mysql/debian.cnf, will use the username
"debian-sys-maint" but the password that is in root's .my.cnf. Also note,
that every change you make in the /root/.my.cnf will affect the mysql cron
script, too.

        # an example of $HOME/.my.cnf
	[client]
	user		= your-mysql-username
	password	= enter-your-good-new-password-here


---

### Post by IncomingFire on 2007-11-05
This is my second really crazy bump for the day, but once again another search on google lead me to this.  "mysql +debian-start" is the google search that led me here.

So same problem as the first poster.

Solved with:
```

sudo apt-get purge mysql-server-5.0
sudo apt-get install mysql-server-5.0

```

EDIT: My guess is with my problem, that maybe there were some old .debs left on my system after upgrading to 7.10 that the system used instead of d/l the new ones....or maybe not that doesn't make sense, it should be able to tell the difference between what apt is pointing too and what was already on my system.....I dunno.  I just hack at things till they work lately.

---

