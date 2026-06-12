---
title: "server - no server"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by den_elze on 2006-11-07
hi,

I installed ubuntu 6.10 yesterday, and configured it like I prefer. But today I descided that I also want to use it as a web and ftp server. Do I have to remove ubuntu 6.10 and replace it with ubuntu 6.10 server? Or can I do exactly the same with the standard edition? but add vftpd and apache2.

thx,


Koen

---

### Post by ctrlcctrlv on 2006-11-07
Well, hmm

I have been sucessfully running Apache2 as a web server on a regular Ubuntu Dapper install. I was wondering the same thing myself. I think the idea is that you can just install a server with no graphical interface, unplug the moniter and leave it running.

I think you can do either depending on what you are trying to do i.e. develop on a desktop or run service.

but..im not really an expert and you may ewant a second opinion

paul

---

### Post by Chayak on 2006-11-07
No you don't have to reinstall.  It's the same thing except the server install is stripped down and the kernel it uses is tuned for that specific task.  You can just install the server packages you need and run it on your machine without any issues.  To be honest you wouldn't see the difference in server performance with the desktop kernel unless you have a higher activity server.  If you do install the server kernel you'll take a hit on desktop performance as it gives priority to the system and not the user.  I'm not going to go into specifics on the kernel as I would probably only succeed in confusing you :P

---

### Post by randomi on 2006-11-07
> **den_elze said:**
> hi,

I installed ubuntu 6.10 yesterday, and configured it like I prefer. But today I descided that I also want to use it as a web and ftp server. Do I have to remove ubuntu 6.10 and replace it with ubuntu 6.10 server? Or can I do exactly the same with the standard edition? but add vftpd and apache2.

thx,


Koen

You can continue with your current installation as long as you have space left on your root partition to install everything that you want to install. You can use synaptic to install all of the servers that you want (ftp, http, etc.) and also anything else that you may want (php, mysql, etc.) and have it all run on your current install.

---

### Post by StormNet on 2006-11-07
You don't have to re-install ubuntu just to make it run as a web server. The advantage of the server install is that it is a LAMP (Linux Apache MySQL and PHP) installation out of the box, without anything extra (such as a GUI) so you will have to do the configuration through the command line. When you are new to linux, you may want to stick with the regular install and just install the needed packages.

It isnt that hard to install the necessary files to add the necessary packages to run a web server and ftp.

[Ubuntu Server Guide]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/index.html") has good guides on installing the different packages that you may need.

---

### Post by OriUbu on 2006-11-07
Not being new to how all these things work. I tried as said and as would be normal practice of apt-get install mysql-server etc, etc being new to Ubuntu I followed the server guide mysql works on first install but after a reboot will now not start just fails.

So there might be something in using the server version and adding the desktop

---

### Post by StormNet on 2006-11-07
I am currently running apache, php and mysql on my laptop and my server machine which i installed on a regular ubuntu install. I am managing mysql using phpmyadmin, just to make things a bit easier. what kind of errors are you getting on your mysql install?

---

### Post by OriUbu on 2006-11-07
I get no error on install all works fine until I reboot then the socket just wont come up. I'm using 6.10 x64 

Just get the following

> 
orignboy@ori-ubuntu:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail] 
orignboy@ori-ubuntu:~$

orignboy@ori-ubuntu:~$ cat /var/log/mysql.log 
orignboy@ori-ubuntu:~$ 

orignboy@ori-ubuntu:~$ /usr/bin/mysqld_safe start
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[31773]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[31778]: ended
orignboy@ori-ubuntu:~$ 



That's about as much as I get. :(

---

