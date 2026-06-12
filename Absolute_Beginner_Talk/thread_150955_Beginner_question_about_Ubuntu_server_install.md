---
title: "Beginner question about Ubuntu server install"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by sean451 on 2006-03-27
Hi, I am new to this whole linux thing.  I am hosting a web server for a friend, and i wanna install the ubuntu server install, but before i do that, i have a few questions.  Up till now I had just a basic debian install, and ssh'ed to it.  I was wondering what is in the ubuntu server install?   Is it just like the debian install?  or does it come with stuff already installed(ssh, ftp, apache....)

---

### Post by harisund on 2006-03-27
AFAIK, the Ubuntu server is merely a stripped down version of the regular Ubuntu, and it simply misses the GUI. What doesn't get installed in the regular version doesn't get installed in the server version too. 

For one, it doesn't come with SSH Server (only a client), FTP, Apache etc.. You will have to install them using apt-get (easiest way.)

What I do is install using the server option, do a quick apt-get install openssh-server. Then I  can start logging in from another machine and using it. Much easier that way.

---

### Post by gymsmoke on 2006-03-27
Check out the How To Forge... 
[www.howtoforge.com](www.howtoforge.com)
there's a couple of great ubuntu server installs in there (step by step)...

---

