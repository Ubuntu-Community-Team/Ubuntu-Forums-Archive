---
title: "MySQL Database Beginner"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by stoopid on 2007-03-26
I use SQL and MySQL from 1and1.com.  I need an application (not a web based one) that will allow me to view tables, create queries, forms etc.  Much the same way Access does.  

Do you have any suggestions?

Thanks.

---

### Post by fakie_flip on 2007-03-26
apt-cache search mysql | less

That will search all available packages in the repositories for mysql in the name and/or description of packages and display the output in less so you can scroll up and down. If you see a package that may be the one you are looking for, then do this command to get more info on it and substitute its package name.

apt-cache show packagename

---

### Post by goghgoner on 2007-03-26
Base is installed as part of the OpenOffice suite. It is the open source database that is most like Access (almost exactly like it). It is relatively new and other than a quick check I haven't created a db in it, yet. I read somewhere that you can connect it to a Mysql database and than use it for forms and queries in that way. That sounded appealing to me.

---

### Post by gh0st on 2007-03-26
I use MySQL administrator and it works great for me. It runs well in Gnome and allows you to manage your MySQL servers in a nice GUI.

To install it just do the following:

```
sudo apt-get install mysql-admin
```

It should show up under the "System Tools" on your menu under Edgy.

Hope it works for you :)

---

