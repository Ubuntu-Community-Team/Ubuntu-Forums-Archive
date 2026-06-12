---
title: "Apache2 httpd.conf authentication ..."
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-09-10
Hi,

I have my web server up and running (Thanks Ubuntu LAMP!) ... is really easy ... however:

I can't quite get a handle on how to use Apache2 to authenticate some of the directories in my www folder (note: I have a symbolic link pointing from /var/www to /home/damon/www so I can easily access my web documents via SSH/AFP).

I have read that I can do .htaccess files for each folder, or -- better yet -- to make a change in the httpd.conf file ?  

Basically, I have a folder called /www/pvt/ ... I want to get that little drop down authentication thing happening ... 

Thoughts ?

D

---

### Post by kidders on 2006-09-11
Drop down authentication?

Google .htaccess for some general instructions on authentication over HTTP. What kind of authentication are you interested in exactly? Would you like your usernames/passwords to be checked against /etc/shadow perhaps?

Post the kind of thing you'd like to have happen, and I can give you more specific help :-)

On a related topic, you might have noticed that apache can give you access to your users' homes via [http://my.host.name/~username](http://my.host.name/~username) as well.

---

