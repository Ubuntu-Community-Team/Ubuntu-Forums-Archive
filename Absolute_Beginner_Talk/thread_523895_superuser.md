---
title: "superuser"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by reivan15 on 2007-08-12
Hi i have downloaded a Catalyst control center and when i try to install it it says Run with super user please help i searched for this problem but nothing works

---

### Post by Bagster on 2007-08-12
put the sudo command in front of whatever command you are using to install the program ie 

sudo apt-get install catalyst


it wont be exactly like that, but just put sudo at the front and you should be ok

---

### Post by Blutack on 2007-08-12
I assume you have tried
sudo whatevertheinstalleriscalled

if you have and that didn't work then type
sudo su
to switch to the superuser account
then run the installer.

---

### Post by reivan15 on 2007-08-12
Well im new to linux. ive tryed ''sudo /reivan/desktop/Cataylst'' please give me the exsact code im a realy big noob

---

### Post by ptader on 2007-08-12
Can you post the output from the following command:

sudo -l

(that's a lowercase letter "L", not  the number one).  It should ask for your password.

Example session:

ptader@raptor:~$ sudo -l
Password:
User ptader may run the following commands on this host:
    (ALL) ALL


The program, sudo, let's you run commands temporarily as the "superuser" or more accurately, as the "root" user.  The command above will tell us what  your user ID is allowed to run as root.  

..more later,

---

### Post by Blutack on 2007-08-12
If you can see it on your desktop (this is the default if you downloaded it in firefox)
First type
cd /home/reivan/Desktop
then
sudo ?name of the catylst thing

---

