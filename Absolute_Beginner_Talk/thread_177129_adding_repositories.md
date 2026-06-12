---
title: "adding repositories?"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by Aximilli on 2006-05-15
So in order to get my dual monitor setup working, i think i need to add the universe and multiverse repositories. What does that mean, and how do I do that? Thanks

---

### Post by K.Mandla on 2006-05-15
This will explain it better than I could offhand:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Cheers!

---

### Post by rado_london on 2006-05-15
HI. These are the types of repositories containing different programs. To enable the repos firee up a terminal and the following:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Then modify the files so it hasnt got any # in front of all lines beggining with deb. For example
```
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```
should look like
```
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```
Then save th edocument and close it. Again in terminal do:
```
sudo apt-get update
```
Now you have all repos.

---

### Post by Aximilli on 2006-05-15
Thank you very much.

---

