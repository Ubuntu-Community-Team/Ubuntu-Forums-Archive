---
title: "Super-user?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by baLes on 2006-12-13
Hi, I am new to Linux. I just installed Ubuntu and I am trying to install some ATI drivers I just downloaded. The problem is when I try to run it, I get an error saying I need to be Super-user to do this. So I tried going back to the login screen and logging is as root but it said I wasn't able to login root from that screen. So basically I have two questions (maybe the same answer to both?). How can I access Super-user to install my drivers, and how can I login to my root account. Thanks.

---

### Post by taurus on 2006-12-13
Use sudo instead...

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And for your ATI graphic card, check out this guide (after nVidia)...

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by ciscosurfer on 2006-12-13
EDIT: Mr. taurus beat me to the punch!

Welcome to Ubuntu Forums!

Generally speaking, we don't like to log in as root on Ubuntu.

What version are you using: Dapper or Edgy?

In Dapper you have to enable the root account.  In Edgy, the root account is there already but you have to give it a password.

For all your Superuser needs, simply use sudo in a terminal shell, like this```
sudo aptitude install amarok
```Similarly, if the .deb file is on your Desktop, you can simply double-click and a password box will appear where you enter your password.

It's not safe to run your computer as root.  That's how bad things happen!  It's best to let the 15 minute window of sudo (from within an open shell) do the work for you.

---

### Post by aysiu on 2006-12-13
Just preface whatever command with the word *sudo*

Read more here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

