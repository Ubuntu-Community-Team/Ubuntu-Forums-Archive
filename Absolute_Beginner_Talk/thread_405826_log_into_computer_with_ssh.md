---
title: "log into computer with ssh"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Mike1971 on 2007-04-10
Hey Dannyboy79,

Here it is, I have created the new thread and pasted your instructions for SSH.


sudo aptitude install ssh

then that's it. it should install it and start it. to check type this in a terminal

sudo netstat -pat

if you see ssh than you at least have it listening. now make sure it's secure. either you can use password authentification which isn't very secure or you can use public/private keys which is harder to setup but way more secure. if you just want to use password authentification its easy and I can help you with that, MAKE SURE YOU BACK UP THIS FILE FIRST. that would be
sudo cd /etc/ssh/sshd_config /etc/ssh/sshd_config-backup
now lets edit it: gksudo gedit /etc/ssh/sshd_config
make sure you have this:
PasswordAuthentication yes
and also make sure you have this:
# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication no
PubkeyAuthentication no
allowusers yourusernamehere
MaxStartups 10:30:60 #this will prevent outside attackers from trying to connect over and over if they trying to run a script and attack you
then save it and exit. also, this is leaving the default port which is 21. that setting is towards the top. if you have a router and want access to your ssh server from the outside, then you need to forward port 21 to your internal ip address. don't forget this is very unsecure but if you user a very smart password using characters and letters and upcase and lowercase letters it would take a script like 20 years to crack into your computer so its still ok. but this password is the same as your users password so if that one isn't secure you should change it OR set it up using public/private keys. that's more than I want to help with at this very moment. I am fixing a customers computer and need to get it done so I have to go. just gogle ssh using public key and you'll find a guide without a doubt or seach the ubuntu forums. good luck

---

### Post by dannyboy79 on 2007-04-10
i only wanted to start a new thread so that I could help you within it. I have already done that within rthe cd/dvd thread so you really didn't need to do tyhis but now that you have I guess it's good. It's just another ssh thread to join the probably more than 100 that already exist within this forum. 

did you get it to work?

---

