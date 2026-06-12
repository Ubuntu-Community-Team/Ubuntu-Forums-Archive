---
title: "webmin not in repo's"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by byenary on 2007-11-19
Does anybody know why webmin is not included in ubuntu's repo's ?

---

### Post by hyper_ch on 2007-11-19
there might be many reasons for it... maybe there's no maintainer for it... maybe webmin is not considered stable/secure enough... maybe ....

---

### Post by skymera on 2007-11-19
have you enabled extra repos?

system > admin > software sources

tick all boxes :)

sudo apt-get update
sudo apt-get upgrade

---

### Post by louieb on 2007-11-19
Don't know why either. I got the deb from sourceforge.
[http://sourceforge.net/projects/webadmin/](http://sourceforge.net/projects/webadmin/)


---

### Post by daengbo on 2007-11-19
I think it was dropped after Dapper. The interface required the root password, anyway, which Ubuntu doesn't have.

---

### Post by ByteJuggler on 2007-11-19
Might be relevant for you: [https://answers.launchpad.net/ubuntu/+question/17240](https://answers.launchpad.net/ubuntu/+question/17240)

---

### Post by byenary on 2007-11-19
Thing is im able to install it, no problem, but i was wondering why such a fine handy app is not included in the repos (apperantly it has been in the repo till dapper but was than removed for some reason. Webmin does require root password indeed but you give your root a password so i don't understand the problem.

---

### Post by ByteJuggler on 2007-11-19
I think you'd better ask for the reasoning behind that, on Launchpad where the people responsible may be able to comment and/or you might be able to convince them to include it again perhaps.

---

