---
title: "I Have A MySQL Problem - I think it's easy to solve, but I'm a beginner"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by nbrabham on 2008-01-09
I have a mysql problem

Let's start by saying I "inherited this problem" so please talk to me like I'm a child and not an idiot :lolflag:

A router was changed and now I need to change the Mysql to the new IP address.  I don't quite know how to go about it.  I read the info on other post, but nothing I saw answered my question.

Thanks and remember like a child not an idiot.

---

### Post by zipperback on 2008-01-09
> **nbrabham said:**
> I have a mysql problem

Let's start by saying I "inherited this problem" so please talk to me like I'm a child and not an idiot :lolflag:

A router was changed and now I need to change the Mysql to the IP address.  I don't quite know how to go about it.  I read the info on other post, but nothing I saw answered my question.

Thanks and remember like a child not an idiot.


Since you inherited this problem, then I strongly suggest that you configure the mysql server to act in a secure manner.


For security reasons you should be running your mysql server to use the localhost ip address.

Your scripts that you run on your website and such all should be requesting it's local server.

```


sudo gedit /etc/my.cnf file 

[mysqld]
bind-address=127.0.0.1


```

Save the above changed, Then restart mysql

- zipperback
:popcorn:

---

### Post by nbrabham on 2008-01-09
gedit doesn't that suppose to have an option?  I tried what you told me, but it didn't work.

Anyway I saw in the file that local host was modified to the old ipaddress....

---

### Post by nbrabham on 2008-01-09
It's working you did it!  YAY Thanks a lot!

---

