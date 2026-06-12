---
title: "Problems conecting via SSH"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by chibiusa255 on 2006-09-22
I'm have a problem connecting to a box on my LAN via SSH. I've installed the Open SSH client and server on the new box and have changed the sshd_config file for "PasswordAuthentication yes" but i can't log in from any of the other boxes on my network. I can log in locally on the box I'm trying to conect to so I know that the sshd is running correctly but when I try to connect from any of the other machines it prompts me for my password and after three failed attempts it says "Permission denied (publickey,password).". 
I know that the password is correct so I'm assuming it has something to do with the publickey. Any help here would be appreciated.

---

### Post by compwiz18 on 2006-09-22
I'm no expert, but are your usernames the same on both computers?  Otherwise it might be trying to use the wrong username, so even if the password is correct...

---

### Post by chibiusa255 on 2006-09-23
The usernames are the same for both machines. I always use "ssh [email]username@192.168.1.xxx[/email]" anyway, so, I don't think that's the problem.

---

### Post by YeahBuntu on 2006-09-23
did you open the port you chose for SSH in the ' built in firewall ' in Ubuntu?  

I am using firestarter and im very new to this but I know a little about networking and it sounds like your being denied access to SSH from a firewall ... simply installing SSH does not open the port.


Thats my guess.

noobs helpin noobs

---

### Post by chibiusa255 on 2006-09-23
I'm not running a firewall and if the connection was being blocked by a firewall I don't think I would be getting far enough to be prompted for my password. 
I have another box that I set up at the same time as the one I'm having problems with and everything's working fine with it. 
Since I only installed yesterday I may just take it down and reinstall everything. I know that's a pretty drastic solution but all I have to lose is the half-hour or so it takes do it.

---

