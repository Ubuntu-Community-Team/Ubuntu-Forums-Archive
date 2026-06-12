---
title: "Keeping track of activities on a User Account on our Ubuntu computer"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by hanzj on 2008-03-24
we're setting up a new account on our computer.

 is there a way to keep a log of all visited internet  websites of that new account?

 and when they log in, and when they log out?

---

### Post by dcstar on 2008-03-24
> **hanzj said:**
> we're setting up a new account on our computer.

 is there a way to keep a log of all visited internet  websites of that new account?

 and when they log in, and when they log out?

/var/log/user.log will show you user activity.

Please don't use unnecessary formatting in your posts - some people will deliberately ignore posts posing for "attention".

---

### Post by hanzj on 2008-03-24
Understood. I've removed any formatting that was inadvertently carried over when I copied and pasted my text.

---

### Post by hanzj on 2008-03-24
user log doesn't show internet activity.

---

### Post by hanzj on 2008-04-09
bump

---

### Post by ad_267 on 2008-04-09
If the browser being used is firefox then the files you want to keep track of will be in /home/username/.mozilla/firefox

In this folder on my computer there is a subfolder called "n6l4uq0x.default." I'm not sure if this is what it would be called for you but under this directory are:

history.dat contains the users browsing history
cookies.txt could also be useful

The user can delete their browsing history and cookies however so this might not be what you want

---

