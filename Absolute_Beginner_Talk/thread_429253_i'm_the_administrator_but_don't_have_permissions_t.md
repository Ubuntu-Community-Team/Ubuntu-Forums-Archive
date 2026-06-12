---
title: "i'm the administrator but don't have permissions to access my filesystem! [Resolved]"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by solipsist_hero on 2007-05-01
Hi Folks,

I just installed Ubuntu the other day. I use it at work so I'm familiar with it at a basic level, but only as a user with permissions in just my home directory.

As I have installed Ubuntu on my own desktop, my account is obviously the admin account. If I go into Users and Groups I have all the admin user priviledges. However, when I downloaded Thunderbird and decided to install it in my /usr directory and tried to make a folder for it, it told me I couldn't. So I looked at my access for the filesystem and it tells me that it belongs to root and I can't do anything about it. Whereas if I go to my home directory then I can change permissions etc. Am I coming across here?

I've attached a screenshot to show my priviledges.

If anyone could help me out with this, I'd really appreciate it. It seems to defy logic, but I'm sure there's something really simple that I'm missing.

---

### Post by darkrose on 2007-05-01
hello,

Your account is still a regular user account, in order to modify anything outside your home directory, including installing new applications and make directories.

You can open the file browser as root by opening tha terminal and running:

gksudo nautilus

You'll have to enter your password and then you'll have root access to the file system, and can do anything. This is just an extra layer of security, and also helps prevent you accidently deleting the entire file system!

---

### Post by aysiu on 2007-05-01
This will help you out:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

So will this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by solipsist_hero on 2007-05-01
Cool thanks that sorted that issue for me :)

> **darkrose said:**
> hello,

Your account is still a regular user account, in order to modify anything outside your home directory, including installing new applications and make directories.

You can open the file browser as root by opening tha terminal and running:

gksudo nautilus

You'll have to enter your password and then you'll have root access to the file system, and can do anything. This is just an extra layer of security, and also helps prevent you accidently deleting the entire file system!

---

