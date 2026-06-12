---
title: "how do i reset the password for phpmyadmin / mySQL?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by yellowband on 2006-08-02
Hi
in my attempts to get myth TV working, i'm stuck at the part where i set a pssword/user for mySQL and phpmyadmin.  When i type localhost in the web browser, and click on phpmyadmin, the login page appears.  I'm supposed to leave th user as "root" and the password blank, but when i click to enter, i get an error message.  I don't recall setting a password for this.  In fact, i just removed evertying mySQL related, then reinstalled it, and still the same problem.  

can anybody tell me how to reset this password?  thank you

---

### Post by adamkane on 2006-08-02
Try a blank password.

I had trouble with mysql in mythtv remembering any of the settings, so I had to bag it for the time being.

---

### Post by yellowband on 2006-08-02
ya, that's what i said, i tried a blank password, but it says 

"#1045 - Access denied for user 'root'@'localhost' (using password: NO)"

I found an article at the mySQL site about resetting a root password, but it is WAY over my head.  could there be something simpler going on?  i have just started using mySQL so i don't care about losing any data or anything.

---

### Post by adamkane on 2006-08-02
I can only recommend that you start with a new mysql install. That is uninstall, then re-install mysql.

If you can post the instructions for resetting the password, I may be able to interpret it for you.

---

### Post by fredanthony on 2006-09-08
I know this is old but I recently ran into this issue. Here is how I resolved it:

1) Stop mysql:
> $ /etc/init.d/mysql stop

2) Make sure that all of the MySQL processes are actually stopped or killed. You can check for running MySQL processes with this command:

> $ ps waux

3) If any MySQL processes are still running, they will look similar to the following:

> 2102 32523 ... /bin/sh /usr/local/mysql/bin/safe_mysqld ...
2102 32557 ... /usr/local/mysql/libexec/mysqld --basedir= ...

You can kill the processes with the kill command(Note: The second column is the Process ID or PID):

> kill -9 32523

4) Restart mysql with --skip-grant-tables: 
> $ /usr/bin/mysqld_safe --skip-grant-tables

5) Open a new seesion, leave the other open as well, in the new session:
> $ /usr/bin/mysql

6) This should get you in, now:
> use mysql;

7) Once you are using the mysql database, run the following:
> UPDATE user SET Password=PASSWORD('YOUR_PASSWORD_HERE') 
WHERE Host='localhost' AND User='root';

8) now quit out with quit; and then restart mysql:
> $ /etc/init.d/mysql restart

Thats it, you should now be logged in.

---

