---
title: "GUI admin for MySql and PhP"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by blimp89 on 2007-08-27
Hi folks,

I'm very new to Linux. 

I just installed Ubuntu server and then a GUI interface on top of it. The server came with Apache, MySql and PhP.  
I dont know how to access the SQL server via some kind of GUI so that I can build a database. 

All in all, I dont know how to get to Mysql, Apache web server and PhP. Someone suggested PhpAdmin.  I downloaded it, but how do I install it?
And I think it is web based and probably needs to go to the root directory of the apache server?

I know these are very basic questions but I'm really new at this and havent a clue what to do.

Many Thanks

---

### Post by mevets on 2007-08-27
phpmyadmin is a great tool. To install it, it's easiest if you run this from the terminal:
> 
sudo apt-get install phpmyadmin


---

### Post by KCPokes on 2007-08-27
PhpMyAdmin is priceless from a developer standpoint.  To further simplify, in my opinion, your server administration tasks, you may want to look into Webmin as an option.  It can be installed with a 

> sudo apt-get install webmin

---

### Post by louieb on 2007-08-27
I just got my LAMP server going. phpmyadmin is the repositories. You can use Synaptic to install it.   Can't remember what  all I did but I i used [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP") as my guide. I got a [website up and running on my toy]("http://louieb.isa-geek.net/").

---

### Post by mevets on 2007-08-27
I tried to install webmin from the repos and it told me it wasnt there...

oh btw, blimp, apache by default is going to be serving documents from '/var/www'

---

### Post by louieb on 2007-08-27
> **KCPokes said:**
> ... Webmin as an option... installed with ** 			 				sudo apt-get install webmin ** 

I'm running feisty  and have all my repositories enabled.  A Synaptic search  did not find **webmin** however a Goolge search did find this [Installing Webmin On Ubuntu Feisty Fawn (7.04) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty").  I am going through it now to see if I can get webmin up and running.

---

### Post by KCPokes on 2007-08-27
Sorry, I did install it via a package from the Webmin website (webmin.com).  I was thinking I had found it in the respository, but obviously I was wrong.  Sorry for the confusion, but still worth the install.

---

### Post by louieb on 2007-08-28
> **KCPokes said:**
> ...but still worth the install.

I agree. Got webmin up and running.  Very  nice.

---

