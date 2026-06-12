---
title: "Cannot fully UN-install PostgreSQL"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by gezus on 2007-04-19
Dist,

Yesterday I initially installed PosgreSQL 8.1 and the Postgre-Client-8.1 using the apt-get and this worked flawlessly.  I then decide I wanted to upgrade to 8.2, I again did this using apt-get.  So now I made a rookie mistake of having 2 Database servers on my box.  So I attempted using the apt-get remove commands to remove both and then re-install only 8.2.

Well the Remove appears to work, however when I re-install no errors are produced but it is not fully installed (i.e. /etc/postgresql/8.2/main does not get created, neither does an executeable inside of /etc/xinit.d/).

*Edit*  I now have it fully uninstalled however when I re-install only /usr/lib/postgresql /usr/share/postgresql
are created, no /etc directories exist at all.  

If anyone has any insight it would be greatly appreciated.

Regards,
Sean.

---

### Post by LaRoza on 2007-04-19
When you want to install dependencies or remove all of a program and its dependencies, don't use apt-get, use aptitude.

---

### Post by gezus on 2007-04-19
I understand, and have done that.

But I still have the same problem that after I re-install the only directory's created are

/usr/lib/postgresql /usr/share/postgresql

But during the install nothing changes, and nothing gets created in /etc at all.

---

### Post by LaRoza on 2007-04-19
I only have used MySQL so I don't know about your server woes, but I have more than one server, web and db, installed on one machine and I don't have any problems. I just have to make sure they are not all running at once on the same ports.

Now that you are having installation problems, try changing the post title to something like "Installing PostgreSQL woes"

---

