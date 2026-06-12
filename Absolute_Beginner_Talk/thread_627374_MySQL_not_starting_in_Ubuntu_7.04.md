---
title: "MySQL not starting in Ubuntu 7.04"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by jainanchal on 2007-11-30
Hello All...

I am trying to start mysql on ubuntu...
it was working fine..but all of a sudden it just stopped working by itself and now that when i am trying to restart it, it is giving me this:

**Warning: World-writable config file '/etc/mysql/my.cnf' is ignored**

doesn't anyone know what is wrong...

actually to be more specific...the socket file: /var/run/mysqld/mysqld.sock given in the my.cnf is not present at that adderss...

do u know if this file can exist anywhere as well?

---

### Post by hyper_ch on 2007-11-30
my.cnf is word-writable and hence a security concern. Fix it by:

```

sudo chmod 0644 /etc/mysql/my.cnf

```

---

