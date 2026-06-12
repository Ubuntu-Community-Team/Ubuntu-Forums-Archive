---
title: "can't start aplications"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by Tanchistu on 2006-03-31
I can't start applications>add aplications, I click on it but nothing happents, why?

and I can't run System --> Administration --> Login Screen Setup

---

### Post by engla on 2006-03-31
[QUOTE=Tanchistu]I can't start applications>add aplications, I click on it but nothing happents, why?

and I can't run System --> Administration --> Login Screen Setup[/QUOTE]
Make sure that your user is a sudoer, that is, the user is in the admin group and in the /etc/sudoers file

If this was the first user created in a normal install, this should all be set up.. Add Applications should ask for your **user** password and start.


However, it's very possible that you did an expert install -- if you did, your normal user won't be setup as a sudoer, you have to do that yourself.

---

### Post by Tanchistu on 2006-03-31
I think I was until I tried to enable root account, I can't modify that file, how do I log as an root, I want to make some changes on another partition and I can't as a user.

---

### Post by Tanchistu on 2006-03-31
So how do I make myself a sudoer again?

---

### Post by pro003 on 2008-01-26
type in terminal:

# sudo -s

and enter your user password that you've supplied during installation of your ubuntu


that's it pretty much,ha?

---

