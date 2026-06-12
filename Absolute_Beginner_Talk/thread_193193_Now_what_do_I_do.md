---
title: "Now what do I do?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by frankjg on 2006-06-09
After installing 5.1.0 and finding out the problems with USB and mounting a floppy I thought I would try a upgrade to 6.06. 

Now I see that I have to start all over from scratch.

Since I just got the CD from Ubuntu a few days ago guess I am missing something.

What worked, worked well but why to have to start all over to upgrade.

---

### Post by Xzallion on 2006-06-09
What do you mean you have to start all over from scratch?  If you got Ubuntu Breezy 5.10 installed, I think you only have to do this to upgrade from 5.10 to 6.06

```
sudo apt-get dist-upgrade
```

Could you please clarify why you think that you have to start all over to upgrade?

---

### Post by Jagot on 2006-06-09
You don't need to start again - you can upgrade from Breezy:

[http://www.ubuntu.com/testing/dapperrc#head-13e42de40d3e6a8ef0b94d9b8441b8466d449471](http://www.ubuntu.com/testing/dapperrc#head-13e42de40d3e6a8ef0b94d9b8441b8466d449471)

---

### Post by taurus on 2006-06-09
You don't have to start over if you want to run Dapper Drake!  You can upgrade your Breezy by modifying your /etc/apt/sources.list...  However, since you said that USB and floppy don't work on Breezy and you just installed it not long ago, a fresh install of Dapper is a good idea then.  Either upgrade from Breezy to Dapper or install Dapper fresh is up to you!

---

### Post by brentoboy on 2006-06-09
first, let me recommend downloading and installing a fresh dapper.
it is one thing to update an existing system that is all setup like you like, but an existing system with no special data or configuration that has issues -- this is a good time to do a fresh install.

that said, doing an update to dapper is perfectly possible from within a breezy install.

open a terminal, and run this:

sudo cp /etc/apt/sources.list /etc/apt/sources.breezy
(makes a backup, just in case)

sudo gedit /etc/apt/sources.list
change all the occurances of breezy to dapper
and save it.

sudo apt-get update
sudo apt-get dist-upgrade

go find a good book, and get cozy

---

