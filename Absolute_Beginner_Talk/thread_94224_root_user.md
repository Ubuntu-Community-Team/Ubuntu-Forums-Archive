---
title: "root user"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-11-23
Hi,
I just finished installing ubuntu. During the installation I was aksed for a user name (my first name) and password and that's the id/pwd I logged in as.
I was wondering how to sign in as root, or am I allowed to sign in as root?
Shouldn't only root have access to the certain files and settings?

Also, while I am here, what is "wiki"??

Thanks.

---

### Post by AlexMartinius on 2005-11-23
The root account is locked. There are files and directories only root has acces to. If you need root access, you just type 'sudo the command' in a terminal (like sudo apt-get update). You will be asked for your password, which is the password you entered during the install (the same one you use to log in).

---

### Post by sigma2805 on 2005-11-23
ubuntu, by default, doesn't let you login to the root account through the graphical login. For all commands through terminal you can use "sudo" and whenever it asks for you password for example to change network settings you enter your password. If you really really really REALLY want to login as root through the graphical login, then in the menu

System -> Administration -> Login Screen Setup

enter your password then under the security tab choose the forth option, "Allow root to login with GDM" then close.

Again, i wouldn't recommend allowing root user login. EVERYTHING is available through sudo. Also, a wiki is a collaborative way to document things. anyone can edit pages, anyone can add content. Check out [Wikipedia]("http://www.wikipedia.org") which is a collaborative encyclopedia...its awesome :)

---

### Post by aysiu on 2005-11-23
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by NoBullMan on 2005-11-23
Thanks a lot guys! I will be bugging you more and more as I dive in deeper.

---

### Post by aznboi on 2005-11-23
[QUOTE=NoBullMan]Thanks a lot guys! I will be bugging you more and more as I dive in deeper.[/QUOTE]

its ok i do it all the time...

---

### Post by d1337 on 2005-11-23
While working in a terminal, it's also nice sometimes to maintain sudo priviledges while working.  To do this, you may open a terminal under your username/password and then "sudo su", at which time you'll be prompted for the password again.  This will keep you from having to type sudo prior to each command, whether apt-get or other.  Once you logout, methinks it hangs on to your sudo priveledges for sevral minutes.  I found this quite helpful while apt-get installing many packages as I was rather used to the vanilla Debian way of running as root.

d1337

---

