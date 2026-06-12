---
title: "Change username"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by ndyguy on 2007-04-12
I was wondering if there was a way, under Dapper Drake 6.06, to change your username.  I've tried under "Users and Groups", but the option seems to be disabled.  I would just delete it and make a new one, but I don't want to loose my settings.  Thanks.

---

### Post by sailor2001 on 2007-04-12
system/admin/users & groups  add another user (name you want) and delete old one

---

### Post by caffienefree on 2007-04-12
[http://mojora.wordpress.com/2007/03/21/linux-change-or-rename-user-name-and-uid-user-id/](http://mojora.wordpress.com/2007/03/21/linux-change-or-rename-user-name-and-uid-user-id/)

---

### Post by ndyguy on 2007-04-12
The second reply was helpful.  I did the following:

sudo usermod -l new-login old-login
sudo mv /home/old-login /home/new-login

That went fine.  However, when I tried to login it said it couldn't find /home/old-login, would I like to login as root or under safe-mode (which I had to do to under my previous steps).  What am I missing?

---

### Post by caffienefree on 2007-04-12
sudo vipw

Make sure your new username has the correct /home directory. This is just a vi edit.

---

### Post by ndyguy on 2007-04-12
I figured it out.  For others' benefit I've listed what I did.  Before you try this you should probably make a new user with admin privileges first so you can easily undo changes you've made.  This is what I did (may not be in exactly sequential order):

In terminal:
sudo usermod -l newname oldname
sudo mv /home/oldname /home/newname

Under System/Administration/Users and Groups:
(optional)  make new group under Groups tab with the same name as newname
select user newname, then Properties
under Advanced tab:
(optional) select your new group (newname) for Main group
change Home directory to /home/newname

Restart computer or restart X (errors will occur until you do this)

---

