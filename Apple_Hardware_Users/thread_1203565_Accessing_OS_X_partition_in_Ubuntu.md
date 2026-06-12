---
title: "Accessing OS X partition in Ubuntu?"
date: 2009-07-03
forum: Apple Hardware Users
---

### Post by [Rolamoto] on 2009-07-03
I have my Early 2008 MacBook (4,1) running a triple boot (OS X, Windows 7, and a wubi-installed Ubuntu 9.04). I can see the majority of my OS X partition, but I can't access my media folders. Is there any way I can access them under Ubuntu?

---

### Post by WA_Garrett on 2009-07-03
Is it that you can't see them or you just can't do anything with the files in them?

---

### Post by [Rolamoto] on 2009-07-03
> **WA_Garrett said:**
> Is it that you can't see them or you just can't do anything with the files in them?

I can't access anything deeper than /users/bmccue/ except Sites and Public.

---

### Post by Richardcavell on 2009-07-05
Is the problem that you are being denied access?

You want your Linux user id (uid) to be the same as your OS X userid, and then you will be able to supply your OS X password to get into the directories.

Richard

---

### Post by [Rolamoto] on 2009-07-05
Yeah, I'm using the same userid and password on both and it says it's a problem with permissions.

---

### Post by cyberdork33 on 2009-07-06
> **'[Rolamoto] said:**
> Yeah, I'm using the same userid and password on both and it says it's a problem with permissions.
your osx username and ubuntu username are still different users. You can change the permissions on the OS X side to allow access to other users. 

You can also change your ubuntu uid (this is a number, not your username) to match that of your OSX user; this will make the system see them both as the same user.

---

### Post by [Rolamoto] on 2009-07-06
Thanks, I got it.

---

