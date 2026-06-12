---
title: "Configuring Tomcat, Apache, PhP and MySQL"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by welshboy on 2006-12-08
Hi guys,

Me again,  I've been out of linux for a good long while, as I was writing something for someone that had to be done in Windows.  

I have installed Apache, Tomcat, Java, Php, Perl and MySQL using the Synaptic package manager, and it all went off without a hitch.

What I want to learn is how do I configure these to run on my linux box?  I've managed it under windows without too much hassle, but I really want to learn how to do it in Linux.

Everything is installed, so I just need to know what to put, into what, and where to put it.

Many thanks :)

---

### Post by welshboy on 2006-12-08
Ok, quick update,

I've got Apache and Php pretty much working, so that's no longer an issue, but Tomcat still is, so any help would be awesome :)

If you lived locally I'd buy you a beer

---

### Post by kno712 on 2006-12-08
My MySql installation works out of the box. To access the MySQL client just go to the command line and type mysql -u root -p and press enter (this was the default password in my installation; you can change it latter, of course, doing "sudo mysqladmin -u root password -p" plus the new password;  it will ask you for the old one after that).

The MySQL server should be already working; otherwise just type sudo /etc/init.d/mysql start.

I recommend you to install the whole bunch of MySQL: mysql-client, mysql-server, mysql-admin, mysql-browser.

All the best

---

### Post by welshboy on 2006-12-08
hey Kno,  yeah I installed all the other mySQL stuff and that now works too, however I'm still stuck on configing Tomcat, I'm not sure what it is I'm doing wrong.

---

### Post by welshboy on 2006-12-08
Sorry folks, just saw the problem.  I didn't know linux put Tomcat on port 8180, windows has it on 8080, but no problems.

Many thanks for the replies :D:D:D:D

Have a nice day

---

