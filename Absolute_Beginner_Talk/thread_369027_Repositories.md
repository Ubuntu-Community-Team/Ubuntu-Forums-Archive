---
title: "Repositories"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-24
I have been using Ubuntu for more than a month. I like it very much. Before I dive into any software installations outside the "Main" respository, I would like some input from those who know about respositories. I read that there are 4 different respositories. Given that some are free and others are not, some have been "certified" and some have not, what can you share with me about repositores? Should I go outside of main? Why? Any other input would be appreciated. Thanks

---

### Post by STREETURCHINE on 2007-02-24
you will no doubt have to get differant packages from the repo,s once you start to install programs.
the one's that come with ubuntu are quite safe
main 
universe
multiverse
backports

i dont know what packages are in each repo's so i activate all of them,
if you want to edit your source list use

      ```
gksudo gedit /etc/apt/sources.list
``` 
and unhash the extra repo,s
then

      ```
sudo aptitude update
                sudo aptitude upgrade
```

:)

---

### Post by rbradshaw on 2007-02-24
thanks for the help. what is the purpose of repositories? how do I use them? what should I know about them other than what was stated earlier?

---

### Post by irish_flu on 2007-02-24
I think this page will anwer your questions:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by r4ik on 2007-02-24
Maybe this

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

explains a bit.

---

### Post by irish_flu on 2007-02-24
By the way; something I noticed in your first post:

Some of the repositories are "non-free", but that means the software contained in them is not "open source"; it doesn't mean that they cost money to use.

---

### Post by Maestro23 on 2007-02-24
For good measure: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

