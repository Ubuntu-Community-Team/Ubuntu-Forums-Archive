---
title: "Setting up LAMP in Feisty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by rookshop on 2007-10-19
How do I set up lamp in 7.04. Have tried it before but failed. A detailed explanation would be highly appreciated.

---

### Post by Qwerty_ on 2007-10-19
This should point you in the right direction.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by rookshop on 2007-10-20
I entered the following in the terminal
```
sudo tasksel install lamp-server
```
But it is stuck at "Installing packages" Please Wait... at 0% for the last 2 hours.

What do I do?

---

### Post by louieb on 2007-10-20
> **rookshop said:**
> I entered the following in the terminal...

That how I installed lamp. I guess the servers are full from people getting Gutsy. May just want to wait it out or try again later.

Might try System>Admin>Software Sources.  Click on the download from . Chose other.
Then click **select best server**.  That might work for you.

---

### Post by Qwerty_ on 2007-10-20
Edit : Just realised user above posted this.



Ive got an idea for you rookshop go to System>Administration>Software Sources

Once you are there change your repositories.

You do this by clicking download from and selecting a mirror that is closer to where you live or one that is not the main server as this is currently being hammered with updaters.

Alternatively once in the Download from menu click the best server button which will select the server that gives you the fastest download.

---

