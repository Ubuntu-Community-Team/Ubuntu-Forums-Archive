---
title: "permissions"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by traveler-1 on 2007-06-10
How do i get permission to write or change a file. It says I do not have permission. I am the only user on this system.

I am having update problems and found the problem ib the list file but can't save changes.

1st time user so make it as simple as possible :popcorn:

---

### Post by meborc on 2007-06-10
if you are using terminal then just use "sudo" in front of the command

read more - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

if you need to work with nautilus, then start it from terminal "sudo nautilus" then insert your password

to change your sources.list open terminal and type "sudo gedit /etc/apt/sources.list" then enter password

---

### Post by Outrunner on 2007-06-10
> **meborc said:**
> if you are using terminal then just use "sudo" in front of the command

read more - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

if you need to work with nautilus, then start it from terminal "sudo nautilus" then insert your password

gksudo nautilus is recommended(it's better to use gksudo for graphical apps)

---

### Post by traveler-1 on 2007-06-10
Thanks for the help and the quick replies. 

Got it working.:p

---

