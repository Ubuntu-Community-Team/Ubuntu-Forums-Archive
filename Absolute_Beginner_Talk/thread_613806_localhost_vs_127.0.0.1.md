---
title: "localhost vs 127.0.0.1"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by the gnome on 2007-11-15
Are these not synonymous in Ubuntu?  I have run into several situations where one works but not the other constantly and it's starting to drive me up the wall.  When should I be using one versus the other?

Sooner than starting to use my laptop as a frisbee or running back to XP in utter frustration, I thought I'd post the question here.

---

### Post by dfreer on 2007-11-15
They should be the same, unless there is something wrong with your /etc/hosts file. What situations are you running into where they aren't working?

---

### Post by Inxsible on 2007-11-15
> **dfreer said:**
> They should be the same, unless there is something wrong with your /etc/hosts file. What situations are you running into where they aren't working?They are the same unless you mucked with it.

EDIT: Whoops, too late ;)

---

### Post by Hospadar on 2007-11-15
it's possible that some apps mishandle localhost if they are poorly written, like if they error check for a number or something like that.

---

### Post by the gnome on 2007-11-15
I was connecting to a remote mysql DB through a tunnel.

This worked:
 > mysql --host=127.0.0.1 --port=2501 --user=me -p

This didn't:
 > mysql --host=localhost --port=2501 --user=me -p


Then I had the exact OPPOSITE behavior connecting to a local DB through a ruby on rails app.

This worked:
> development:
  adapter: mysql
  database: SBE
  username: user
  password: password
  host: localhost
  socket: /var/run/mysqld/mysqld.sock


This didn't:
> development:
  adapter: mysql
  database: SBE
  username: user
  password: password
  host: 127.0.0.1
  socket: /var/run/mysqld/mysqld.sock


Contrary to prior comments this is a straight install, I haven't mucked with anything.

---

### Post by Inxsible on 2007-11-15
> **the gnome said:**
> This didn't:```
development:
  adapter: mysql
  database: SBE
  username: user
  password: password
  host: 172.0.0.1
  socket: /var/run/mysqld/mysqld.sock
```
Contrary to prior comments this is a straight install, I haven't mucked with anything.you know you have 172.0.0.1 as opposed to 127.0.0.1

---

### Post by the gnome on 2007-11-15
Yah typo in the message only, I'll edit it.  That's what I get for rushing.

---

### Post by dfreer on 2007-11-15
Knowing the contents of /etc/hosts might provide us with some insight to your problem.

---

