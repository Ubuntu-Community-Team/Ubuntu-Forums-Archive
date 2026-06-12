---
title: "how do i run this command?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-16
deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

this was a step in upgrading my software..i typed just this and it said it's not a valid command. what do i need to do?

---

### Post by 23meg on 2006-06-16
It's not a command, it's a repository line that has to go into your sources list file. You have to open to edit your sources.list file add this line to the bottom and save the file. ```
sudo nano /etc/apt/sources.list
```After this do a ```
sudo apt-get update
``` and install the packages.

---

### Post by shanepardue on 2006-06-16
thank you! i knew it was something silly, but i'm still learning!

---

