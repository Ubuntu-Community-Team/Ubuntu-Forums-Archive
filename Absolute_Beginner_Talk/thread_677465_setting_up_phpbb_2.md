---
title: "setting up phpbb 2"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-24
Ok, so i've set up the apatche server with php and mysql. i used [this]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") site to do it. and ALOT of help from my wonderful ubuntu family! Now i can only think of one more thing that i need. I need to install phpbb but idk what to put into all those blanks to complete installation? can someone please help me out?

Thank you so much to my ubuntu family!
RadiationHazard

---

### Post by RadiationHazard on 2008-01-24
Can someone please help me??:(:(

---

### Post by Zeroangel on 2008-01-24
First of all, you need to make sure that MySQL is set up. My guess is that its already installed, but you need to set a root password. This is not too hard to do. Refer to this thread:

[http://ubuntuforums.org/showthread.php?t=13245](http://ubuntuforums.org/showthread.php?t=13245)

And read the post by blixtra. It will tell you how to set up the password for the 'root' user.

Once this is done, you have enough knowledge to fill in the blank fields. Which would typically be:

**DSN**: localhost
**Database Name**: *Call this any name you want. I just typically use the name "phpbb"*
**Database Username**: *This is typically 'root' since its installed on your own computer*
**Database Password**: *This will be whatever you set up if you followed Bixtra's steps*


As far as the stuff in Admin setup goes, its all straightforward, set the email to the email you want notifications to be mailed to (ie: your personal email address). Not sure what it is asking about the script path stuff, but if the default doesnt work try using the absolute path that your phpbb install is stored in (ie: /var/www/forum)

Also I suggest that you install phpMyAdmin , you might need this later on if you want to back up your databases and edit things in them without using the command line.

Also, quick question, why are you using PHPBB2? and not PHPBB3 or another forum software?

Just from personal experience I find phpBB2 a nightmare to maintain and upgrade in the long run (doing lots of modifications will prevent forum upgrade scripts from working properly, and if you aren't upgraded your forum is vulnerable to hacking -- this means that upgrading almost guarantees that you'll need to hand-edit lots of files).

---

### Post by RadiationHazard on 2008-01-24
Thank you for the reply.
when i just tried to do the first step it messed up??
screen shot below.......

---

### Post by RadiationHazard on 2008-01-24
ok someone please help! 
why is no one wanting to help me???
:(

---

### Post by RadiationHazard on 2008-01-24
ahhhhhhhhh!!
:(
someone pleaseeeeeeeeee help me!!
it can't be that hard for someone who knows what they're doing...:confused:

---

### Post by RadiationHazard on 2008-01-24
Ok, so i think it's installed wrong. what's the code to uninstall so i can start over?

---

### Post by emarkd on 2008-01-24
Anything you install with:

```
 sudo apt-get install whatever
```

can be removed with

```
 sudo apt-get remove whatever
```

One note:  if you're intending to try and start from scratch, you have to specify that you want the configuration files removed also.  You do that like this:

```
 sudo apt-get remove --purge whatever
```

---

### Post by RadiationHazard on 2008-01-25
i really want to get this before i go to sleep. which i need to already have done. so please hurry and help me! ok i already have mysql installed put when i go to put in the first command used to make a password i get this error. what do i do?

---

### Post by emarkd on 2008-01-25
Is it running?  What do you get from:

```
sudo /etc/init.d/mysql status
```

---

### Post by RadiationHazard on 2008-01-25
i got that it was stopped...

```
jordan@jordan-laptop:~$ sudo /etc/init.d/mysql status
 * MySQL is stopped.
jordan@jordan-laptop:~$ 
```

why'd it stop or was it ever started? =\

---

### Post by emarkd on 2008-01-25
Don't know but

```
sudo /etc/init.d/mysql start
```

will start it

---

### Post by RadiationHazard on 2008-01-25
thanks. i'm getting another error now!
haha, i wish this was easier!!
or that i know half as much as you guys!!

**_Error:_**
```
jordan@jordan-laptop:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
jordan@jordan-laptop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
jordan@jordan-laptop:~$ 




```

---

### Post by emarkd on 2008-01-25
What do you get when you do:

```
mysql -u root -p
```

---

### Post by RadiationHazard on 2008-01-25
it asks for a password. but i don't think that i've created a mysql pass yet?


```
jordan@jordan-laptop:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
jordan@jordan-laptop:~$ mysql -u root -p
Enter password: 


```

---

### Post by emarkd on 2008-01-25
Ok, try this:

```
mysqladmin -u root password newpass
```

where newpass is what you want your password to be

---

### Post by RadiationHazard on 2008-01-25
these errors are getting really old! =/

```
jordan@jordan-laptop:~$ sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [ OK ] 
jordan@jordan-laptop:~$ mysqladmin -u root password (where i put my password)
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
jordan@jordan-laptop:~$ 


```

---

### Post by emarkd on 2008-01-25
You sure you didn't previously set a password?  Even if you uninstall/reinstall mysql, your password may still be saved.  Your install seems to be acting like you've already got a password for mysql's root user.

If you think there's any possibility of this, [this guide ]("http://www.debianadmin.com/recover-mysql-database-root-password.html")may help.

---

### Post by RadiationHazard on 2008-01-25
I just started puting in all the codes i could think of!
did i get it???
```
jordan@jordan-laptop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 33
Server version: 5.0.45-Debian_1ubuntu3.1-log Debian etch distribution

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

```

---

### Post by emarkd on 2008-01-25
Yeah!!  You've already set your password at some other time.  Now that you know the password, you can change it if you want by doing:

```
mysqladmin -u root -p oldpass newpass
```

from the command line. First type quit to mysql and hit enter.

---

### Post by RadiationHazard on 2008-01-25
If it's not one ting it's another!!! =|
ok so now that i've got mysql finally settled after working on it most the day. now all of a sudden i can't put up my site anymore. like when i do it wants me to download the file of the page. now what do i do. i'm really sorry for all the questions! and thanks for all the answers! click here to go to [http://radiationhazard.ath.cx/]("http://radiationhazard.ath.cx/") (my site i'm trying to make.) i'm trying to get up phpbb and when you go to it it should be the install screen. is it? or does it ask you to download it too. and what's wrong why's it asking me to download instead of going to the site?? it worked before...

---

### Post by hoist1138 on 2008-01-25
I second that,
I was having trouble with this earlier tonight and I forgot I set a mysql password a while back....

try the link above to reset?

---

### Post by RadiationHazard on 2008-01-25
what do you mean?

---

### Post by hyper_ch on 2008-01-25
ps: Why not installing PHPBB3?

---

### Post by RadiationHazard on 2008-01-25
I don't know...but I just installed phpbb 3.
but it still trys to get me to download a phtml file everytime i go to the site...
:confused::(

---

### Post by lespaul_rentals on 2008-01-25
Remember that the server refers to "index.html" by default.  Do you have a file in your **/var/www** directory called "index.html"?

Make sure you put it in the **/var/www** directory.

You may have to restart your Apache2 server, like so:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by jayjaygibbs on 2008-03-09
just incase anyone is still interested seeing as it didn't look like their was a solution to this, there is a really good step by step guide on how to install phpbb on ubuntu and it tells you how to setup a database step by step using a database gui tool
[phpbb_guide]("http://www.pluckypigeon.com/phpbb.html")
it's pretty simple:)

---

