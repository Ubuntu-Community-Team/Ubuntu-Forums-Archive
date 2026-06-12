---
title: "Installing MySQL"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by billvb on 2006-05-17
Hi,

I'm having problems (](*,)  - All afternoon) installing and running MySQL.  I understand that some MySQL components come packaged with ubuntu and I downloaded and installed everything else that looked related to it.  My question is, now what?  I tried downloading it from the mySQL site, and read the tutorials about how to install, which were useless to me.  I just want to get the daemon up and running and be able to start building a database.  Any help, or links to any good tutorials would be great. thanks


Also, on another note..  how do i log in as root?  I typed su but i don't know what the password is --- i was never prompted to set one when i installed.

---

### Post by Alcibiades Mystery on 2006-05-17
[QUOTE=billvb]Hi,

I'm having problems (](*,)  - All afternoon) installing and running MySQL.  I understand that some MySQL components come packaged with ubuntu and I downloaded and installed everything else that looked related to it.  My question is, now what?  I tried downloading it from the mySQL site, and read the tutorials about how to install, which were useless to me.  I just want to get the daemon up and running and be able to start building a database.  Any help, or links to any good tutorials would be great. thanks


Also, on another note..  how do i log in as root?  I typed su but i don't know what the password is --- i was never prompted to set one when i installed.[/QUOTE]

I'm having the same exact issue. Hope somebody helps. To log in as root,

sudo -s -H

when prompted for the password, use the password you used to log into gnome or kde

---

### Post by Mr Fat Bat on 2006-05-18
Password:

if you want to be able to lon in as root then you can set a root password by going:

"sudo passwd root" 

[COLOR=Red]This will allow you to log in as root whenever you need by usiing "su"[/COLOR]

Not sure about the problems you are having with mySQL though, what exactly is the problem you are having?  Not running the daemon?

---

