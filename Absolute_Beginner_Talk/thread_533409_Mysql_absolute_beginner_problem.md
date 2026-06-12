---
title: "Mysql absolute beginner problem"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by notredamemaster on 2007-08-23
Dear all,

I have just installed Ubuntu 7.04 desktop version, then there was update package and I updated all. After that I follow the ubuntu online instruction ([https://help.ubuntu.com/7.04/server/C/mysql.html](https://help.ubuntu.com/7.04/server/C/mysql.html)) 
installed mysql with this command:

sudo apt-get install mysql-server mysql-client

then I follow the online instruction to change my root password by 

sudo mysqladmin -u root password newrootsqlpassword

then

Password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I have no idea why this error comes out. I had reinstalled ubuntu twice just try to solve this problem, and I did a lot of research online, still cannot understand why this happen to my Ubuntu. I just install Unbuntu then I install mysql immediately, this problem is still there. What's wrong?

---

### Post by heimo on 2007-08-23
So, did changing password seem to work? Try running mysql with command
```
 mysql -u root -p
```-u sets user
-p asks for password

EDIT: Sorry, now I can see that it's mysqladmin giving that error. Try adding -p parameter to it... I'm not sure if it takes one.
EDIT2: Yes, it should take -p. I'd try:
```
 sudo mysqladmin -p -u root password newrootsqlpassword
```

---

### Post by notredamemaster on 2007-08-23
> **heimo said:**
> So, did changing password seem to work? Try running mysql with command
```
 mysql -u root -p
```-u sets user
-p asks for password

EDIT: Sorry, now I can see that it's mysqladmin giving that error. Try adding -p parameter to it... I'm not sure if it takes one.
EDIT2: Yes, it should take -p. I'd try:
```
 sudo mysqladmin -p -u root password newrootsqlpassword
```

Thank you for your help.

I just find out this and solve my question:
sudo apt-get --purge remove mysql-server mysql-common mysql-client

sudo apt-get install mysql-server mysql-common mysql-client

In the next step be sure to chance the your-new-password with the password you want!

mysqladmin -u root password your-new-password
sudo /etc/init.d/mysql restart

mysql -u root -p

Now I am going to install php, apache2. Let's if anything would work fine!:guitar:

---

