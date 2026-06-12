---
title: "Permissions Question (OSX/Ubuntu Dual Boot)"
date: 2011-01-21
forum: Apple Hardware Users
---

### Post by Fubini on 2011-01-21
Hi there,

I recently installed Ubuntu 10.10 on my Macbook Pro 6.2.

Right now my repository of music and documents is on my OSX partition in my protected user files. The result is that I can't access those files because my Ubuntu user does not have permission to access my OSX user's file. (When I try to navigate there in a terminal I simply get "bash: cd: Permission denied".

However, I am able to invoke sudo to get at the files I want. My question is if there is any way to configure the system so that my Ubuntu user will be able to access those files without having to invoke sudo? 

If at all possible I'd like to keep the file permissions set on the OSX side. Is there any way to tell Ubuntu to just disregard the OSX permissions on those files?

---

### Post by srs5694 on 2011-01-21
You can change your UID value in Ubuntu to match the OS X UID value with the "usermod" command, as in "sudo usermod -u 501 fubini" if your username is "fubini". (OS X normally uses UID 501 for its first user.) That said, I'm not sure this is possible if you're currently logged in as fubini. Thus, you might need to create another administrative account or activate direct root logins to do this. You should also check to see if permissions on your home directory and files have changed, and if not, change them with "chown". (Use the "-R" option to change recursively, as in "sudo chown -R fubini: /home/fubini".)

---

