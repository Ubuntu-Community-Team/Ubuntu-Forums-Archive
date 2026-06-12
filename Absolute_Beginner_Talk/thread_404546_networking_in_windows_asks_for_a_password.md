---
title: "networking in windows asks for a password"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by bronevaya on 2007-04-08
when i network to my windows machine I get propted to enter a user name and password on my windows machine if I want to open a folder on my ubuntu machine. Whats the default password, or how can I change that?

Also, ubuntu is named something crazy on the network, why cant it just be what I call my machine? how can I change this info?

---

### Post by jhenager on 2007-04-08
From your description, your windows machine wants your ubuntu username/password.
I don't really don't do windows much anymore, except at work, so I can't help you with your second question. Post it if you get an answer.

---

### Post by gipsytony3 on 2008-01-07
if ur windows machine prompts for a username and a password to access ur ubuntu-machine shared files and u dont know the password .. u can simply open the terminal type the command:
sudo smbpasswd  
then u must enter the password of the root 
after that ur asked for a new password, then ur asked to retype it .. this will change the password for the current user .. 
when windows prompts for the username and the password ... the username is simply ur username of the ubuntu machine .. and the password is the one u've chosen ..
 good luck ..

---

