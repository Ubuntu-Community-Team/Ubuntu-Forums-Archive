---
title: "problem with installing mysql5 and firewall"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by null123 on 2005-12-01
Hello! 
I try to install latest mysql and run it as a server.
I followed instructions from here
[http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html](http://dev.mysql.com/doc/refman/5.1/en/installing-binary.html)

and did all this
shell> groupadd mysql
shell> useradd -g mysql mysql
shell> cd /usr/local
shell>sudo gunzip < /path/to/mysql-VERSION-OS.tar.gz | tar xvf -

problem is that i get lot's of error messages. First one is that 
command mkdir cannot be excecuted permission denied. And other problems are caused by that there is no directory.

Why is that so? I used the sudo still...? 

I have the basic ubuntu gnome, do i have firewall installed or not? 

Can someone help?

---

### Post by penguinman007 on 2005-12-01
I am also installing MySql.

I plan to click on the client application, open it up and configure the database through a nice gui.

Someone please let me know when I can do this in Linux.
Until then I'll use windows XP.

---

### Post by Robgould on 2005-12-01
You can use the previous version of MySQL in lunx now.  It is available through synaptic.  
 
Here is a thread about compiling MySQL 5. 
 
[http://ubuntuforums.org/showthread.php?t=93725]("http://ubuntuforums.org/showthread.php?t=93725")
 
I hope this works for you.  It is a how to, but a little loose around the edges.  Do you have to use 5?

---

### Post by null123 on 2005-12-01
Thanks, I read that already, but didn't follow that because I don't know at all those commands and what they do.
For example this command: 

*sudo apt-get install make build-essential*

installs some packages, what packages and why do I need them?

I don't need to use mysql5, but i think that was the recommended version by [http://dev.mysql.com/downloads/](http://dev.mysql.com/downloads/) , why not to use it then?

---

### Post by Robgould on 2005-12-01
The version in synaptic installs easily and works well for what most do.  If you have not need for stored procedures of triggers, then the update is not incredibly important.  That is just my opinion, I am sure that others will disagree.  I know that if you compile and install yourself you will not get synaptic updates for MySQL, and you may break somehting else on your system.  I also know that MySQL will not be backported.  To me, it just made more sense to run the current version in synaptic (there are actually 2....4.0 and 4.1 I think).

---

