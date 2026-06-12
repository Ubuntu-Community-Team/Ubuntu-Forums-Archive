---
title: "I cannot get mysql setup properly"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-08-31
I'm trying to set up mysql on a remote server through ssh.  I've followed the tutorials [here]("https://help.ubuntu.com/7.04/server/C/mysql.html") but I always get the same error.  

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I'm not sure what it means or how to fix it.  Regardless, I can't install/configure mysql.  Any help?

---

### Post by funrider on 2007-08-31
what was the command you use before you get the error message?

---

### Post by TheOrangePeanut on 2007-08-31
nelson@beta-pc:~$ sudo mysqladmin -u root password mypassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
nelson@beta-pc:~$



That is immediately after I sudo apt-get'd mysql-server and mysql-client.  mypassword, of course, isn't what I'd really use, but I used that just to demonstrate what I was doing.

---

### Post by funrider on 2007-08-31
have you set up the password by the way (the configuration part)?

---

### Post by TheOrangePeanut on 2007-08-31
No, that is what I was trying to do.  Trying to set the root password threw that error message at me.

---

### Post by southernman on 2007-08-31
That tut is seemingly a little outdated... IMO. Try this link to the mysql manual for setting up the initial accounts on a fresh installation.

[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html]("http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html")

---

### Post by Chayak on 2007-10-27
I'm getting the same errors myself.  This isn't the first time I've set up mysql on a webserver and to be honest this is a little frustrating as it's holding up deployment.

```

mysqladmin -u root password *examplepassword*

27ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

sudo mysqladmin -u root -h localhost password *examplepassword*

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

This is a fresh 7.10 install so I'm left scratching my head.

So I did a version check, guess what? Same error

```
mysqladmin -u root version
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

---

### Post by fishmonger on 2007-10-28
I'm in the same spot.
What I have figured out is that the default configuration has no password  for the root user.  So you can log into the database with just 'mysql -u root'.  However, changing/enabling the password has been harder than I thought it would be.  The commands in the documentation: 

shell> mysql -u root
mysql> SET PASSWORD FOR ''@'localhost' = PASSWORD('newpwd');
mysql> SET PASSWORD FOR ''@'host_name' = PASSWORD('newpwd');

These don't work.  I assume it's because of the table structure.  I'm not all the familiar with SQL.  From poking around in the tables, I can see the user 'root' in the different hosts (localhost, etc) with a blank password, but I'm leery of changing it to just cleartext in the table.  I figure there has to be some command for that and I just can't find it.

edit: I'm just an idiot and the 'mysqladmin -u root password XXX' command worked.  Duh.

---

### Post by Chayak on 2007-10-28
It's good that some people are getting it to work but I'm still getting an ERROR 1045 that it can't connect despite that fact the service is running.

---

### Post by herbnet on 2007-10-28
I am a newbee and I too was getting the error.  After playing around for the last hour have come across thiese things:

First try this: mysqladmin status
You should get the error you were getting before. During the mysql-server installation you should've been asked to set a password for root. If you did not when the prompt "Enter password:" shows up hit the enter key.  If you entered a password during the mysql-server installation, enter that password at the "Enter password:" prompt.  So let's see what happen now with adding a parameter to the command you first tried.

mysqladmin -p status
Oaky you should see the "Enter password:" prompt.  After following the instructions above you should see a report back on how mysql is running. Replace status with ping, which should return "mysql is alive."

Enter ps -edf|grep mysql should return around 5 lines of data.  Look for mysql in the first column (about the 3rd line down).  Its job is pointing back to the root job that started it.

Now to change root's password:
mysqladmin -p -u root --password=newpassord  will prompt present the "Enter password:" following instructions above as to what you need to enter at this point

I have to add 1 thing. I did execute apt-get update, followed by sudo apt-get install mysql-server, followed by sudo apt-get autoremove and walked thru the installs for phpmyadmin, apache2, and mysql-client. They reported everything was running latest versions

---

### Post by gkestrel on 2007-11-03
Please bear with me this is my first post.
I had the same problem, even tried uninstalling and reinstalling mysql then found the answer
in the terminal enter     sudo dpkg-reconfigure mysql-server-5.0        this allowed me to set a password for root and the problem was then fixed.  Hope this helps anyone else struggling with this problem

---

### Post by bravo911 on 2007-11-05
> **gkestrel said:**
> Please bear with me this is my first post.
I had the same problem, even tried uninstalling and reinstalling mysql then found the answer
in the terminal enter     sudo dpkg-reconfigure mysql-server-5.0        this allowed me to set a password for root and the problem was then fixed.  Hope this helps anyone else struggling with this problem

I have also been experiencing the same problem... but i ran the above command, and it's not helping at all... i just get an 'unable to connect to localhost' and 'access denied for user 'root'@'localhost'

i'm getting very frustrated with this. There is no visible reason why this does not work... 
grr.

---

### Post by Chayak on 2007-11-07
use ```
sudo dpkg-reconfigure mysql-server-5.0
```

It will let you set the root password and then you can work with it.

then if you use a mysql command be sure to use the "-u root -p" so it will ask you to set the password.

example

```
mysqladmin -u root -p create somedatabase
```

---

