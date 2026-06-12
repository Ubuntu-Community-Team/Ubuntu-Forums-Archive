---
title: "mysql gui tools. dirty fix"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by ralphz on 2007-08-18
Hi

As many of you probably know mysql gui tools don't work properly in feisty. What i have discovered is that when you log in to your mysql server as root everything is working fine. How is that possible?

That would mean that the problem with mysql gui tools not working might be accounted to some kind of mysql server. Any ideas?

Ralph

---

### Post by nexu56 on 2007-08-20
Sorry if you're already aware of this, but you can't log in to mysql with your ubuntu user account.

Mysql has its own user accounts. By default mysql only comes with one user, root. You log in with root (and change the password) then create new mysql users.

---

### Post by ralphz on 2007-08-20
I created the users i need. But using them shuts mysql-administrator and query browser with seg foult

---

### Post by steve.horsley on 2007-08-20
That doesn't happen to everyone. I use mysql-query-browser and mysql-admin almost daily, with no problems. The ones that come with the Ubuntu distro that is.

I know that doesn't help you a lot, but it may help eliminate some possibilities.

---

### Post by hyper_ch on 2007-08-20
what do those tools do? I normally use phpMyAdmin to do all stuff in MySQL...

---

### Post by steve.horsley on 2007-08-21
One is a GUI for doing queries, with an sql panel, a results table panel and a tree of all databases/tables. The other is a GUI for doing admin work - editing users, tables etc. Try them.

---

### Post by hyper_ch on 2007-08-21
phpMyAdmin does both of that... you may want to have a look at it:

```

sudo apt-get install phpMyAdmin

```

And then it should be directly linked in /var/www/phpmyadmin

---

### Post by steve.horsley on 2007-08-22
Do I have to view it in a browser? I'm not sure I like the idea of a a browser based database client - it sounds very clunky.

---

### Post by hyper_ch on 2007-08-22
it is a browser based database client but extremly powerfull... the only drawbacks it has is backuping up and restoring dbs that are larger than the max_memory allocated for a php script.

[http://www.phpmyadmin.net/home_page/demos.php](http://www.phpmyadmin.net/home_page/demos.php)

---

### Post by Wim Sturkenboom on 2007-08-22
> **hyper_ch said:**
> it is a browser based database client but extremly powerfull... the only drawbacks it has is backuping up and restoring dbs that are larger than the max_memory allocated for a php script.

[http://www.phpmyadmin.net/home_page/demos.php](http://www.phpmyadmin.net/home_page/demos.php)
Doesn't it need apache (or other webserve)r as well? If so, that is the first (and probably biggest) drawback.

---

### Post by hyper_ch on 2007-08-22
well, it nees some webserver... apache or lighthttp - I use mysql only with webapplications so that's not a drawback for me.

---

