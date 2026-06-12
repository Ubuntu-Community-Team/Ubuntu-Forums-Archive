---
title: "mysql will only run if i sudo"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by vizitorq on 2008-04-02
hey guys, i'm trying to figure out this mysql thing. i've gone through plenty of tutorials, some worked, some didn't. but i've got it installed just fine. i created a linux group called mysql. i've created a linux user called mysql. but i can't run mysql without doing sudo mysql. and then, it automatically logs me into mysql... i want to do mysql -u mysql -p, and then type in my mysql user's password. it won't even let me login as root: mysql -u root -p... access denied. what the hell. there's defeinitely a loss of translation here. where does linux end and mysql begin? what do you think the problem is?

i'm wondering because i'm trying to use it with phpmyadmin and/or mysql administrator (graphical). but these programs won't connect to my mysql because i don't have the login right and it'll only run in root. what the eff??

---

### Post by louieb on 2008-04-02
I used the instruction here [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
Then installed phpmyadmin and webmin. Probably just need to set yourself up as a user with all privileges granted. The above link has how to do that.

---

