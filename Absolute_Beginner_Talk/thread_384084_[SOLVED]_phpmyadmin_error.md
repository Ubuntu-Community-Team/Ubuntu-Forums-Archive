---
title: "[SOLVED] phpmyadmin error"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-14
I installed mysql via Synaptic package manager.. downloaded phpmyadmin  untared it to /var/www/phpmyadmin, i run localhost/phpmyadmin but get Cannot load mysql extension. Please check your PHP configuration. do i need to set up any configuration for phpmyadmin to work properly?

Thanks, Davey

---

### Post by orkim on 2007-03-14
It sounds like you don't have the mod_php module for apache.  There should be a package for this and upon installing it you should be good to go.  Apache is not able to "process" php files by default without the mod_php module installed.

Hope that helps.

-orkim

---

### Post by DaveyG on 2007-03-14
Thanks for your help, i installed the php5-mysql module wich seems to have fixed the problem. :)

---

### Post by DaveyG on 2007-03-14
Oops.. accidently deleted the root@localhost user..

now i get an error message if you look [here]("http://daveyonline.net/phpmyadmin") is there any way i can fix this?

Thanks, Davey

---

### Post by orkim on 2007-03-14
This is the error that I am seeing:

#1045 - Access denied for user 'root'@'localhost' (using password: NO) 

Typically this is because the root@local host account has a password set but you haven't told phpMyAdmin about it.  There is a phpMyAdmin.conf (maybe .ini) file that contains all the settings which will need to know the password.  If my memory serves correct, it is very well commented and should be pretty simple to correct.

There seems to be a link to setup.php as well, which looks like it might allow for "online" configuration file generation.  There were a few errors in there about not having write premissions.  You could probably fix that temporarly by "chmod 777 phpMyAdmin.conf" (or the correct file) and utilize the tool.  Then be sure to chmod it back to the permissions it was before once you are done.

I hope that helps.  Let me know if there is any more questions.

-orkim

---

### Post by DaveyG on 2007-03-14
im confused.. i had it working til i deleted the databes/account.. i dont seem to be able to uninstall or re-install mysql either.. :confused:

---

### Post by orkim on 2007-03-14
sudo dpkg -r package.name

This will remove a package.  Then you can re install it with an apt-get.

I'm not sure why you were removing accounts though.  Is there some reason?  You should pretty much leave the default accounts alone.  They are there for a reason and shouldn't be deleted.  One thing you might do is set a password on the root account to make it a bit more secure.  That will require updating of the phpMyAdmin file though!

Good luck!

-orkim

---

### Post by DaveyG on 2007-03-14
Still got an error :( .. im getting a little angry with this..

```
davey@davey-online:~$ sudo dpkg -r mysql-server-5.0
(Reading database ... 109330 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ ok ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
davey@davey-online:~$ 

```

---

### Post by orkim on 2007-03-14
> **Davey Goudou said:**
> Still got an error :( .. im getting a little angry with this..

```
davey@davey-online:~$ sudo dpkg -r mysql-server-5.0
(Reading database ... 109330 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ ok ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
davey@davey-online:~$ 

```

Hrm.  Looks like you might have deleted all the users in there?  debian-sys-main@localhost was denied access as well.  I'm guessing that a "/etc/init.d/mysql start" and/or a "/etc/init.d/mysql stop" is not working as well.

You might have to manually add those users back.  You should be able to look at the .deb package (i.e. unpack it) and see the files that are in there.  I'm guessing that you will need to restore the default users file though it slips my mind as to where this is actually stored.  That should be enough to issue a 'start' and get it running.  Then you should be back to square one with the default users.

Again, I've never removed the default users so this is all speculation.  You might want to issue a "ps -ef | grep mysql" to be sure there aren't any instances of the mysql daemon running before messing with the user files though.

I hope that helps.

-orkim

---

### Post by DaveyG on 2007-03-14
right, my friend has some how sorted it out.. got the databases & users there.. trying to set up phpBB 2 and it says: The PHP configuration on your server doesn't support the database type that you chose..

any ideas why?

---

### Post by chuckyp on 2007-03-14
Also just FYI you could have installed phpmyadmin with synaptic or apt-get.  Its in the repos.  sudo apt-get install phpmyadmin

---

### Post by orkim on 2007-03-14
As well as PHPBB.  That will take care of all the dependencies for you too!

"sudo apt-get phpbb2 phpmyadmin"

See what packages it wants to install.  That might clue you into the missing packages.

-orkim

---

### Post by DaveyG on 2007-03-14
Thanks for that but it doesnt recinize the command :( 

```
davey@davey-online:~$ sudo apt-get phpbb2 phpmyadmin
Password:
E: Invalid operation phpbb2
davey@davey-online:~$ 

```

---

### Post by orkim on 2007-03-14
I'm going to assume that's because you don't have universe in your repositories.

Edit /etc/apt/sources.list to include a line like the following:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main universe

(Yours probably looks the same but without the 'universe' on the end)

Issue an "apt-get update"

Then try to install phpbb2 and phpmyadmin once again.

-orkim

---

### Post by DaveyG on 2007-03-14
Bump, Installing some updates... keep you posted on what happens next... hopefuly a good responce.

---

### Post by DaveyG on 2007-03-14
Cheers guys :) got it all working... were would i be without you all? :lolflag:

---

### Post by orkim on 2007-03-14
Glad to hear it.  :)

-orkim

---

### Post by jmrasor on 2007-03-22
Had the same problem. Installer could not stop server; sudo could not, either. To fix it, I force-stopped the mysqld server:

# ps -A | grep mysqld
4354 mysqld
9281 mysqld-safe
# sudo kill 4354
# sudo kill 9281 (on the pids, ymmv)

-- it might take two or three stabs to get those actually killed. Check with ps -A | grep mysql.

# apt-get upgrade phpmyadmin (apt wanted to upgrade mysql-server, and this ran correctly.)

Verify that you can control the server:
# sudo /etc/init.d/mysqld stop
# sudo /etc/init.d/mysqld start

-- since the error while installing mysql-server comes from being unable to stop the server, the way should now be clear if you can stop and start it.

---

