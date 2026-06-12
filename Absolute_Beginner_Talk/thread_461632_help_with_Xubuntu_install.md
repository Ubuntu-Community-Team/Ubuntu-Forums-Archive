---
title: "help with Xubuntu install"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by freefromXP on 2007-06-01
I just installed ubuntu 5.10 server on a dell inspiron 7500 (pii 400)  

   I log in teh console I un commented the universe repository lines I am pretty sure I got them all.

 I did the following

sudo aptitude update
sudo aptitude upgrade
sudo aptitude install xubuntu-desktop

  I get unable to resolve some dependencies

  The following packages have umet dependencies
          xubuntu-desktop: depends: abiword but it is not installable
                                          depends: firefox which is avirtaul package

that was in message along with several otehr programs

What do I do to fix this.

---

### Post by taurus on 2007-06-01
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

However, 5.10 is kind of old so maybe you should consider installing Feisty Faw--7.04.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by freefromXP on 2007-06-01
I guess I can but it's on lap top setting nest to me so I would have to type it in I guess with only the ubuntu server install on it

---

### Post by freefromXP on 2007-06-01
I think I got it but taking # from restricted modules.  I will let you know :)

 It is downloading a bunch of stuff says like 10m in bottum right so it should be good now

---

