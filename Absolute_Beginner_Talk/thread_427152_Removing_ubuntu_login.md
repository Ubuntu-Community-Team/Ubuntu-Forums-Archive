---
title: "Removing ubuntu login"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by gam3r on 2007-04-29
I got a ubuntu box setup with samba as my file server and i use SSH to control it from my windows pc using Putty.

The problem i have is that whenever i turn the fileserver on running ubuntu, it stops at the login screen and then i have to plug in the keyboard and type in the user name and password in order to login to the machine and start samba/ssh.

Is there a way i can make it so it just loads ubuntu without asking me for a Login/PW? I have searched but have found nothing.

Thanks.

---

### Post by mendingo84 on 2007-04-29
Since it is a fileserver, why would you ever power it off?

---

### Post by gam3r on 2007-04-29
It's not completely finished yet you see, i am still trying to get parts of it working so it doesn't have a permanent place as of yet. It's also really noisy(CPU fan)...:(

---

### Post by klytu on 2007-04-29
> **gam3r said:**
> I got a ubuntu box setup with samba as my file server and i use SSH to control it from my windows pc using Putty.

The problem i have is that whenever i turn the fileserver on running ubuntu, it stops at the login screen and then i have to plug in the keyboard and type in the user name and password in order to login to the machine and start samba/ssh.

Is there a way i can make it so it just loads ubuntu without asking me for a Login/PW? I have searched but have found nothing.

Thanks.

This should work in Gnome: Go to  System Menu>Administration>Login Window the select the Security tab and check the box next to "Enable Automatic Login". Then choose a user from the drop-down menu.

---

### Post by Compyx on 2007-04-29
I doesn't make much sense that you have to log in locally to start sshd to allow remote login on a server.
You should add the samba and ssh daemons to a run-level to make them start automatically. Logging into a server should only be used for administrative purposes, not to start processes that should be running anyway.

Exactly how to do this on a Debian-based machine, I don't know. In Gentoo there's a nice 'rc-update' script that handles these things, I would think there's something similar on Debian.

---

