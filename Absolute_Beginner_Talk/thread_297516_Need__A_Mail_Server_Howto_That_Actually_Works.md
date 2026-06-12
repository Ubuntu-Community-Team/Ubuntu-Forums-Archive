---
title: "Need  A Mail Server Howto That Actually Works"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-11-11
would like virtual domains with a mysql back-end... Pop and IMAP4...

there are so many out there...  would like your input one wich one looked best.

---

### Post by huggy77 on 2006-11-11
found one!

i got the following tutorial to work.
[http://www.howtoforge.com/virtual_postfix_mysql_quota_courier](http://www.howtoforge.com/virtual_postfix_mysql_quota_courier)

i did not mess around with the quota part...
IMPORTANT:
the tutorial is lacking a package you have to install: courier-authlib-mysql 
this will give you the authmysqlrc file that allows you to use MYSQL for your users and domans...

also....
READ THE COMMENTS AT THE BOTTOM OF THE PAGES...
in particular:

> user = mail_admin
password = mail_admin_password
dbname = mail
table = domains
select_field = 'domain'
where_field = domain
hosts = 127.0.0.1

and

> You need to create a folder for your users (example for [email]bofh@YOURVIRTUALDOMAIN.com[/email]):

mkdir /home/vmail/YOURVIRTUALDOMAIN.com
mkdir /home/vmail/YOURVIRTUALDOMAIN.com/bofh
cd /home/vmail/YOURVIRTUALDOMAIN.com/bofh
maildirmake Maildir
chown -R vmail:vmail /home/vmail/YOURVIRTUALDOMAIN.com/*


Now you're ready to insert the user into the SQL database. This avoids having mail accepted without a place to put it. After you insert the user into the database, you should be able to login via IMAP and see an empty directory. You should also now be able to send mail!

Be sure to restart everything after making changes...

```
/etc/init.d/courier-authdaemon restart
/etc/init.d/courier-imap restart
/etc/init.d/courier-imap-ssl restart
/etc/init.d/courier-pop restart
/etc/init.d/courier-pop-ssl restart
```

good luck - take your time... dont get frazzled.... CHECK YOUR LOGS...

---

