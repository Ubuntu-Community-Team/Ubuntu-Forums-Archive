---
title: "Problems updating 6.10 after install"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Acupuncture Doc on 2007-03-30
Hi all,

Pretty new to this - 
I installed 6.10 after working with 6.06 for a while. Now after updating on the web and automatix2 install there is a problem.

Whenever updates come over the web and I try to install them, I get an error message that asks me to run the following command.

dpkg --configure -a

I have no idea what that means and when I try to run it on terminal, it tells me I need super user privileges. I seem to recall that the command to become root was su- (at least it was in Fedora) but that asks for a password and when I enter the password I used when I set up the machine, it tells me that authentication failed. 

How do I fix this Y'all? Whats a super user? It it anything like a root user? Is the SU- command out of place here?

---

### Post by ahmatti on 2007-03-30
The superuser command in Ubuntu is sudo so run "sudo dpkg --configure -a"

Ubuntu uses sudo instead of su by default. You can enable su, but it is not recommended.

---

### Post by smbm on 2007-03-30
Try using sudo instead of su. It'll ask you for a password, you just need to enter your password. 

Hope this helps

---

### Post by Woody@N87 on 2007-03-30
I'm VERY new to this myself and don't know anything about the command your trying to run, but every time my puter asks for a password so far it's looking for the my user password, not the one I put in at setup.

---

### Post by Maestro23 on 2007-03-30
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

