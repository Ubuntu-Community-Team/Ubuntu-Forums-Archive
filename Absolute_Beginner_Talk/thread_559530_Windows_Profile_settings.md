---
title: "Windows Profile settings"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by jmeyer on 2007-09-25
[SIZE="2"]I joined my ubuntu laptop to our windows domain.  I am using my windows credentials to logon to our network, but wanted to know how and where my documents and settings on my ubuntu machine would show up in my windows profile?[/SIZE]

---

### Post by upbeat.linux on 2007-09-25
It depends on how you joined to the domain. 

In most cases it will be stored in: /home/<username>/

However, you can edit the /etc/smb.conf file to configure where the profile goes.

---

### Post by jmeyer on 2007-09-25
I put the home dir here:

> template homedir = /home/%D/%U
/home/NST/user_name

when i look in that directory, it only has items I have done locally.  When i log off and it saves to the server where does it save in windows?

---

