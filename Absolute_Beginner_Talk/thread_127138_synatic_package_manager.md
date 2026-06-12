---
title: "synatic package manager"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-02-08
ok i am trying to change my synaptic package manager on ubuntu to look for programs on the internet first since i had a friend install everything of a cd for me. 

Thanks for the help 

Evan

---

### Post by christhemonkey on 2006-02-08
If you edit the file sources.list, and comment out the lines reffering to the CD.
Then start synaptic, it should not detect the CD packages.
```
sudo nano /etc/apt/sources.list
```
Then put a # at the start of the first few lines that refer to CD.

---

### Post by steve.horsley on 2006-02-08
In Synaptic, Settings->Repositories, and un-check the CD repo. 

While you're at it, on that same page, click Settings button and check "Show disabled software sources". Then you can enable the multiverse and universe binary repos, and the backports repo.

---

