---
title: "root password"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by linuxnoob on 2006-01-06
hi,i installed ubuntu on my pc using the default install option...
After installing,i boot up and play with it..and its kinda good...
I just want to login as root but i dont know whats the password because ubuntu didnt ask me for root password upon installation..anybody could tell me what's the root's default password..T.Y.:)

---

### Post by aysiu on 2006-01-06
You don't need to log in as root.
Read the third link of my sig.

---

### Post by Madpilot on 2006-01-06
Ubuntu uses sudo for admin rather than a seperate root login.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) has all you need to know, and more...

---

### Post by Mission 10 on 2006-01-06
Is there any reason for this?

---

### Post by Madpilot on 2006-01-06
[QUOTE=Mission 10]Is there any reason for this?[/QUOTE]

For encouraging sudo rather than root? Read the URL I provided above for all the various reasons - basically it's a security thing.

---

### Post by aysiu on 2006-01-07
[QUOTE=Mission 10]Is there any reason for this?[/QUOTE] Is there any reason to log in as root?

---

### Post by Mission 10 on 2006-01-07
Well i have to log in as root to start firestarter. Not sure why. It's not on the taskbar if I don't. But I usually use sudo su.

---

### Post by aysiu on 2006-01-07
I don't know the exact command for Firestarter, but have you tried Alt-F2 ```
gksudo firestarter
```?

You don't ever *have* to log in as root. Please read the links linked to earlier in the thread.

---

### Post by Mustard on 2006-01-07
I thought firestarter was in the Applications>>System Tools menu after install.

If its not you could always add it there yourself.  Here is a screenshot of my set up.  Use the Applications>>System Tools>>Menu Editor to add it to the menu.

[[IMG]http://img203.imageshack.us/img203/6600/menueditor3tz.th.png[/IMG]](http://img203.imageshack.us/my.php?image=menueditor3tz.png)

---

### Post by graham_hamblin on 2006-01-07
This is the one thing about Ubuntu that I do not like.   Having enabled a root log in I still find that I can install new software etc in my user account without entering the root password.

They have complicated an otherwise excellent system, unnecessarily, and I think it will have the effect of putting a lot of new users off.

---

