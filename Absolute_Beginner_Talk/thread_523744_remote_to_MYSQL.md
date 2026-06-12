---
title: "remote to MYSQL"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by alzoid on 2007-08-12
I just set up LAMP using Ubuntu Server 7.04 as a development server.

I installed MySQL Administrator and Query Browser on the developers machines.

At first I could not connect so I commented out the Bind Address in my.cnf and I could connect.

When I connect using MySQL Administrator I can not add users,  when I click on users I get a access 
denied error.  

The error says SELECT denied for user root@'myip' on table users

I granted permission for root but I get errors when trying to add users etc.  Is there a way to give my root user full access to Administration with the ability to add users etc?

I know the install is secure for good reasons but because this is a dev box I want to be able to let people remote to it and execute scripts.  I also want to administrate it remotely.

Thank you,

Al

---

### Post by Pragmatist on 2007-08-12
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

