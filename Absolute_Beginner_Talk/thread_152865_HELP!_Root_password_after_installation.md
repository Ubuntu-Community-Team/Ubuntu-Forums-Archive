---
title: "HELP! Root password after installation"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by janki on 2006-03-30
I just did my first-ever installation of Ubuntu from scratch, and everything went perfectly. The problem now is that I don't know the root password. During the installation Ubuntu asked me for my name and user-name, but never asked me to type a root password. Now I can't log on as a root user. I tried both the password of my own user and no password at all, but none of these work.

This is probably a very trivial question, but I will appreciate a lot if somebody can help me.

Thanks!!!

---

### Post by Akli on 2006-03-30
Can you at least log in with your username? if you can't it means that you have forgotton your password,

An advice: format, reinstall and choose a simple password.

---

### Post by ferebee on 2006-03-30
[QUOTE=janki]I just did my first-ever installation of Ubuntu from scratch, and everything went perfectly. The problem now is that I don't know the root password. During the installation Ubuntu asked me for my name and user-name, but never asked me to type a root password. Now I can't log on as a root user. I tried both the password of my own user and no password at all, but none of these work.

This is probably a very trivial question, but I will appreciate a lot if somebody can help me.

Thanks!!![/QUOTE]


You don't create a root user with Ubuntu, to do a task that needs root 
user permission, you use sudo instead.

This page in the Ubuntu Wiki explains it better than me ! ;) 
[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by janki on 2006-03-30
[QUOTE=Akli]Can you at least log in with your username? if you can't it means that you have forgotton your password,

An advice: format, reinstall and choose a simple password.[/QUOTE]

I have no problem logging in with my username. I remember the password. And my user has admin privileges (I can install new programs using Synaptic Package Manager). The problem is that I can't log in as user root. I thought maybe it was because I have to create the root user first, but when I try this Ubuntu tells me the user already exists.

---

### Post by Akli on 2006-03-30
Your username is the root, BUT unlike other linux os, ubuntu does not allow you to be root without typing your password in the terminal,

Check ferebee's message, it explains how it works.

---

### Post by janki on 2006-03-30
[QUOTE=Akli]Your username is the root, BUT unlike other linux os, ubuntu does not allow you to be root without typing your password in the terminal,

Check ferebee's message, it explains how it works.[/QUOTE]

Now I get it. :-) Thanks!

---

### Post by engla on 2006-03-30
[QUOTE=Akli]Your username is the root, BUT unlike other linux os, ubuntu does not allow you to be root without typing your password in the terminal,

Check ferebee's message, it explains how it works.[/QUOTE]
No that's  not really how it works. The default user is just a user in the admin group and a sudoer... the root user is a separate user, but root has no password set by default. Hence, it's impossible to log in as root. Enabling root is simply setting a password for root.

---

### Post by spiderbatdad on 2006-03-30
[QUOTE=janki]I just did my first-ever installation of Ubuntu from scratch, and everything went perfectly. The problem now is that I don't know the root password. During the installation Ubuntu asked me for my name and user-name, but never asked me to type a root password. Now I can't log on as a root user. I tried both the password of my own user and no password at all, but none of these work.

This is probably a very trivial question, but I will appreciate a lot if somebody can help me.

Thanks!!![/QUOTE]

you create a root password for yourself by opening a terminal and typing the command        "sudo passwd root "  (no quotes)    you will then be asked to type a password and then re-type it. This will now be your root account password. You can then make yourself root anytime by typing       " su"          and then entering your root password when asked. It is not recommended to create a root password for yourself, rather use the sudo command as mentioned above. Not sure why it isn't reccommended other than security risks from hackers. I use a seventeen letter password not any common phrase or recognizable word order, so good luck to anyone who wants to crack that!

---

