---
title: "Windows Host file equivelent?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2007-06-18
I am trying to set up a local server to test on.  I have it all set up, but I would also like to set certain web pages on that server to look locally for them.

In Windows you would go to the host file and add an entry for that website.  Is this possible to due on linux?

---

### Post by NT4usB on 2007-06-18
same same...open a terminal, type this and read on:```
 man hosts
```

---

### Post by Jhorra on 2007-06-18
I think I must be doing something wrong, I tried both of these. (Actual name of website is replaced)

127.0.0.1/website     [www.website.com](www.website.com)
localhost/website      [www.website.com](www.website.com)

When I try to hit the website, it's still taking me to the actual website.  Do I need to restart something for it to take affect?

---

### Post by bodhi.zazen on 2007-06-18
The file in Linux is : /etc/hosts

The syntax is the same with windows and linux.

---

### Post by Jhorra on 2007-06-18
I know, see my above post.  I tried putting both of those lines in the hosts file, but when I go to the website, it's still taking me to the real website, and not the URL I put in there.

---

