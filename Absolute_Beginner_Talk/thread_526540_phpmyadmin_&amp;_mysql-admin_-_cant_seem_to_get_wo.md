---
title: "phpmyadmin &amp; mysql-admin - cant seem to get working"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-08-15
Greetings,

I am still learning the basics and am having a little difficulty with this darn LAMP stack install.  So here is my current setup and dilemma.

Feisty 7.04, apache2, PHP5, and MYSQL5

apt-get install libapache2-mod-php5
apt-get install php5-cli
apt-get install phpmyadmin
apt-get mysql-server-5.0
apt-get install mysql-server-5.0 libapache2-mod-auth-mysql php5-mysql

I was able to create the index.html in my user folder /home/linux/public_html which _was_ viewable at [http://localhost](http://localhost) but is not any more (Problem 1) caveat -- i can browse to the ip address 10.4.11.51 and view the index.html just fine.  Hmm, so i can see it published, just cannot see it local anymore.  I thought maybe i should restart apache2, but that didnt work.  I used this command: sudo /etc/init.d/apache2 restart  

Problem 2, [http://localhost/phpmyadmin](http://localhost/phpmyadmin) doesnt work (edit) The requested URL /phpmyadmin was not found on this server
Problem 3, [http://localhost/mysql-admin](http://localhost/mysql-admin) doesnt work either (edit) The requested URL /mysql-admin was not found on this server

I did install mysql-admin from the package manager, which seems to work, but was wondering why it isnt connected to my apache server.  Maybe, it doesnt and i just dont know that.  

In any case, any help would be greatly appreciated.  I can post whatever configuration files that we need to help me along.  Thanks in advance.

---

### Post by Clay_Banger on 2007-08-15
i dont have any idea how to fix your problem, but if you are only using the server for testing purposes, I recommend that you use lampp, the linux version of xampp. It installs and runs instantly without any configuring, and has php, mysql, phpmyadmin, ftp and a lot more.

---

### Post by williamburn on 2007-08-15
Thank you, actually that is what i am trying to accomplish.  Can anyone answer me this question, do i need myphpadmin if i can view the sql database through the program mysql administrator?  I see that myphpadmin does the sql administration just via a gui.  

I hate to be a stick in the mud, its just that i am very new to linux and i wanted to see trough the entire install of the LAMP stack.  Its quite frustrating to not have something working.

Again, i appreciate any replys

---

