---
title: "MySQL?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-06-07
I installed Apache2 and ubuntu center; and it's asking for my MySQL database and password; I don't know if I set it up.  Is there anyway I could check to see if it's installed (and then somehow uninstall / reinstall it?  or reset my username and password?)

---

### Post by Robgould on 2006-06-07
Look in synaptic....search for mysql.  It will tell you if its installed.  If it's not installed you can then install from there.

---

### Post by chris062689 on 2006-06-07
It says it's installed; but I do not know what my database and password is..
I want to get ubuntu center working so bad! ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Robgould on 2006-06-07
If you did not set one up...ther is not one.  A default mysql installation has a username "root" with no password.

---

### Post by chris062689 on 2006-06-07
I used root, "" for my username and password....

Not Found

The requested URL /center/install/install2.php was not found on this server.

---

### Post by Robgould on 2006-06-07
Install mysql-admin from synaptic.  It is a gui that will let you manage users and the server.

---

### Post by chris062689 on 2006-06-07
How would I go about creating a new database named ubuntucenter?
Also; is it OK during the installation to have the database location as localhost?

---

### Post by Robgould on 2006-06-07
After you install mysql-admin....give it host name "localhost"  username "root"  password blank....hit connect.
 
this should connect you.
 
from there you can make a new database usne the catalogs section.  And manage users from the users section.

---

### Post by Robgould on 2006-06-07
It just occured to me....also check again what you have installed.  Make sure that mysql-server is installed.  There are several packages to mysql.  You want to make sure you have the server.

---

### Post by adamkane on 2006-06-07
Easiest thing is to use phpmyadmin to add new users. (mysqladmin is a PITA to use.)

First pick a preferred installation and install:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Next open phpmyadmin in your web browser:
[http://localhost/phpmyadmin]("http://localhost/phpmyadmin")

Log in with:
Name: root
Pass: [blank]

Find or add a database. Go to Permissions to add new users.

---

### Post by chris062689 on 2006-06-07
I can't use root , (password: "") because it asks me to fill out all forums, could you step me through how to add a database and password to mqsql?  I've tried looking around in the terminal, but no go.

(Terminal instructions would be best!) ;)

---

### Post by adamkane on 2006-06-07
Too many difficulties with the terminal method, and too many new PHP/MYSQL users to help. The best suggestion is to get comfortable with phpmyadmin.

If your installation is hosed, you may have to re-install ubuntu or keep responding to your threads, until you can find someone who can help.

---

### Post by chris062689 on 2006-06-07
If I had access to phpmyadmin that would be great!
But I can't find it anywhere in the apache2 webfolder.
Is there a way I can install phpmyadmin?

---

### Post by Robgould on 2006-06-07
if you install mysql-admin and mysql-server and you cannot connect to localhost with root and no password then something is wrong with your installation.  I use mysql all the time.
 
Install mysql-server.  Install mysql-admin.  Run admin which should be in your menu now.  You don't have to go to the terminal.  It is a nice gui.  There is a section for users.  A section for catalogs.  A section for the server.  A section for everything you need to do.

---

### Post by chris062689 on 2006-06-07
Alright, I am at MySQL Administrator program, how do I set a new database up for ubuntu center?

(BTW; thank you for all of your help so far!)

---

### Post by Robgould on 2006-06-07
at the bottom there should be a section called "catalogs" or something similar...going off memory.  I there you whould see the databases that exist already.   There are two of them.   Right click on that and you should get an option to add a schema or catalog.  This will be your new database.  
 
If you want to do much more than that....like make tables, etc.  I would install mysql-query-browser and do it from there.  It is much easier.  You connect just like you do with mysql-admin.
 
You can create new databases from query browswer too.  Just right click and add a new schema.  Then select it and add a new table...etc.  If you want to design a database you need more reading than I can give you on here.
 
If you are in admin though....your server is running and you are connecting.  I hope this helps you.

---

### Post by chris062689 on 2006-06-07
Well; in the Ubuntu Center; it keeps on asking for a password (the forum cannot proceed without a password)  how would I set a password to my schema?

---

### Post by Robgould on 2006-06-07
I have never used Ubuntu Center.  
 
In mysql you assign passwords to users and then you assign rights to a shema to that user.  You do that from the user administation part of mysql-administartor.  Click on the user you want and then go to the schema priviledges tab.
 
There has to be  a schema first though.  I would assume that whatever application you are using should create its own.

---

### Post by chris062689 on 2006-06-07
MySQL Details

Please enter your MySQL details
Database Host  localhost
Database User  root?
Database Password  (it doesn't allow a blank here.)

---

### Post by Robgould on 2006-06-07
I would guess it wants you to configure a root password....go to mysql-admn.  Go to users section.  Click on root.  Expand it...there will be an @localhost.  Click on that.  Now on the right you will see a section to set a password for that user.  Set the password and save.  Now you have a [EMAIL="root@localhost"]root@localhost[/EMAIL] password to your mysql server.

---

### Post by Robgould on 2006-06-07
I would guess it wants you to configure a root password....go to mysql-admn. Go to users section. Click on root. Expand it...there will be an @localhost. Click on that. Now on the right you will see a section to set a password for that user. Set the password and save. Now you have a root@localhost password to your mysql server.
 
 
EDIT:  I don't know how I posted this twice.

---

### Post by chris062689 on 2006-06-07
Well; whenever I hit the User's section, the thing says "Loading Profiles.." or something like that, then freezes, I will post console results soon.

---

### Post by otis_u on 2006-06-08
I freeze after the "Users" button as well.

---

### Post by Robgould on 2006-06-08
Are you using breezy or dapper?  I had some troubles with it freezing in breezy.  I never did figure out why.  In dapper it works fine for me.  Sometimes, after unsuccesfull logon attempts is locks up.  I know you should not have to, but restarting sometimes gets it back going.  You could probably kill all the processes related to it and do the same thing.  I'm sorry you are having trouble.

---

### Post by hotbrainz on 2006-06-08
Hey Guys,

I am not an expert at resolving the individual problems that u have posted but, i have been using LAMP without any issues for some time now. I got it running in 15 minutes. You could just do it and chill :)

Please use the link XXAMP in my signature.

Hope this helps :)

---

