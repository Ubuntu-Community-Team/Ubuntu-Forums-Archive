---
title: "MytTV install is killing me..."
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by arnabbiswas on 2007-03-07
Hi,

I am attempting the seemingly impossible task of installing mythTV for the first time and I am getting the following error when running mythTV setup:

2007-03-07 00:05:35.037 Unable to connect to database!
2007-03-07 00:05:35.037 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-07 00:05:35.088 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

](*,) 

I tried resetting my root password as  instructed in the troubleshooting guide at the end of this page:
[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

but I get the following results:
sudo mysqladmin password test
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I am totally stumped. Please help...

---

### Post by superm1 on 2007-03-07
> **arnabbiswas said:**
> Hi,

I am attempting the seemingly impossible task of installing mythTV for the first time and I am getting the following error when running mythTV setup:

2007-03-07 00:05:35.037 Unable to connect to database!
2007-03-07 00:05:35.037 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-07 00:05:35.088 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

](*,) 

I tried resetting my root password as  instructed in the troubleshooting guide at the end of this page:
[https://help.ubuntu.com/community/MythTV_mythtvsetup](https://help.ubuntu.com/community/MythTV_mythtvsetup)

but I get the following results:
sudo mysqladmin password test
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I am totally stumped. Please help...


Okay so the user you launched mythtv-setup with - they were in the "mythtv" group right?  That's the big big important thing before you start going to having to change passwords etc.

---

### Post by arnabbiswas on 2007-03-07
Yes, as indicated by the following command:

pom@pom-desktop:~$ grep mythtv: /etc/group
mythtv:x:115:pom

This shows that the user "pom" is in the mythtv group and this is the user I am using.

---

### Post by superm1 on 2007-03-07
> **arnabbiswas said:**
> Yes, as indicated by the following command:

pom@pom-desktop:~$ grep mythtv: /etc/group
mythtv:x:115:pom

This shows that the user "pom" is in the mythtv group and this is the user I am using.
Okay good.
This might be an obvious question, but i'll throw it out here.  Mysql is running, correct?  As in if you check the running processes, mysqld is working.

Given that you can't connect with mysqladmin is just worrysome.

---

### Post by arnabbiswas on 2007-03-07
The mysql process is running as shown by the following:

 ps xa | grep mysqld
 4314 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 4378 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
 4379 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
31365 pts/0    R+     0:00 grep mysqld


But I think this may be an access issue since I also get the following:

pom@pom-desktop:~$ mysqladmin version
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'pom'@'localhost' (using password: NO)'

Also when I try to login to phpmyadmin/ from [http://localhost](http://localhost) using firefox using username:root and passwd: [blank], I get the following:
Error
#1045 - Access denied for user 'root'@'localhost' (using password: NO)

Looks like something is wrong with my passwords. Any clues please?

If nothing else works, is there a way I can do a clean uninstall of apache, mysql and pmp and reinstall these apps from scratch. I ask because there is something mysterious with my php/mysql install since when I tried to access the phpmyadmin/ link on [http://localhost](http://localhost) yesterday, firefox was always throwing tat "Open .phtml with ..." error. But today tis behavior has mysteriously disappeared.  I have tried a bunch of installs/reinstalls since so I am unsure as to what exactly fixed this. But I am afraid that I may have corrupted soething else so I was just wondering if it would make sense to do a clean uninstall/reinstall of apache,php and mysql. If you think this would make sense, could you please send me instructions for doing so.

My goal is to setup mythTv successfully. Surprisingly, I had a completely smooth IVTV driver install, which is considered to be the hardest part. But this mythtvsetup is just  driving me nuts.

---

### Post by Scorpuk on 2007-03-07
One thing it might be is the database password is not set correctly in mythfrontend for the user you are runnign the program with.


Couple of questions:

1. What user did you install MythTV under?
2. What user are you trying to run MythTV under?


When I installed MythTV I found that I had no problems running MythTV under my mythtv user (As described in Garry Parkers site [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")), but if I then switched over to my main account I could not successfully connect to the mysql database. 

When I checked the settings of mythfrontend it actually had my username and password set to "mythtv", but that was the wrong password. I had to log back on as my mythtv user and run the frontend from there to find out what the password was as this was generated during the setup process.



So to run MythTV I need to have the following:

Logged in as MythTV user (as used in installation)
Computer IP address and database IP address set to localhost in mythtv-setup

and all seems to work a treat.


One of these days I'll actually get time off work to try and sort it out as I am thinking this will prevent me from logging in remotely across the network and streaming live TV to another computer. :(

---

### Post by arnabbiswas on 2007-03-07
Ahh, so I was doing this wrong - I had installed myttv as well as running mythtv-setup as root. I follows the guide you mentioned and changed the mythtv password and added mythtv to all the groups as asked. 
But now when I log  in as mythtv and try to run the setup I get the following error:

mythtv@pom-desktop:~$ mythtv-setup
mythtv-setup: cannot connect to X server 

Wat could be wrong?

---

### Post by WakkiTabakki on 2007-03-07
You usually get that error if you try to run an X-app as a different user than you've logged in as (through gdm).
If you logged in as "yourself" in gdm, started a terminal and su:ed as user mythtv and then started mythtv-setup, you would get this error...
Instead, try:
```

me@pom-desktop:~$ **xauth +**
me@pom-desktop:~$ su mythtv
Password:
mythtv@pom-desktop:~$ mythtv-setup

```

/N

---

### Post by arnabbiswas on 2007-03-07
Thanks WakkiTabakki. I will try this when I get home from work and report findings.

---

### Post by arnabbiswas on 2007-03-07
This did not work,. Looks like ubuntu does not like the "xauth +" command:

pom@pom-desktop:~$ xauth +
xauth: (argv):1:  unknown command "+"
pom@pom-desktop:~$ xauth
Using authority file /home/pom/.Xauthority
xauth> exit
pom@pom-desktop:~$ su - mythtv
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mythtv@pom-desktop:~$ mythtv-setup
mythtv-setup: cannot connect to X server 

Any help for this noob highly appreciated.

---

### Post by WakkiTabakki on 2007-03-08
> **arnabbiswas said:**
> This did not work,. Looks like ubuntu does not like the "xauth +" command:

pom@pom-desktop:~$ xauth +
xauth: (argv):1:  unknown command "+"
pom@pom-desktop:~$ xauth
Using authority file /home/pom/.Xauthority
xauth> exit
pom@pom-desktop:~$ su - mythtv
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mythtv@pom-desktop:~$ mythtv-setup
mythtv-setup: cannot connect to X server 

Any help for this noob highly appreciated.
I'm an idiot, sorry.
I should be **xhost** not **xauth**...

/N

---

### Post by arnabbiswas on 2007-03-08
Unfortunately this did not work either:

pom@pom-desktop:~$ xhost +
access control disabled, clients can connect from any host
pom@pom-desktop:~$ su - mythtv
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mythtv@pom-desktop:~$ mythtv-setup
mythtv-setup: cannot connect to X server 


Also, I tried xhost+localhost with the same result:

pom@pom-desktop:~$ xhost + localhost
localhost being added to access control list
pom@pom-desktop:~$ su - mythtv
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

mythtv@pom-desktop:~$ mythtv-setup
mythtv-setup: cannot connect to X server

---

### Post by arnabbiswas on 2007-03-08
Further information:

I am able to launch mythtv-setup as the regular user after adding this user to the mythtv group using this command:

pom@pom-desktop:~$ sudo usermod -a -G mythtv pom

But then the mythtv-setup fails as before :

2007-03-08 05:59:10.409 Unable to connect to database!
2007-03-08 05:59:10.409 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-08 05:59:10.482 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

Sorry for being stuck with something probably very basic but I need some help to get going here.

---

### Post by arnabbiswas on 2007-03-08
Anyone please?

I would really like to tame the MythTV beast and would appreciate any help I get.

---

### Post by superm1 on 2007-03-09
> **arnabbiswas said:**
> Further information:

I am able to launch mythtv-setup as the regular user after adding this user to the mythtv group using this command:

pom@pom-desktop:~$ sudo usermod -a -G mythtv pom

But then the mythtv-setup fails as before :

2007-03-08 05:59:10.409 Unable to connect to database!
2007-03-08 05:59:10.409 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-03-08 05:59:10.482 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...

Sorry for being stuck with something probably very basic but I need some help to get going here.

Okay. as long as you *havent* changed the mysql password for the mythtv mysql account, then 
rm ~/.mythtv -rf
And try again after being in the mythtv group.

Putting you into the mythtv group gives you permissions to read the file that stores the mysql password for the mythtv mysql account in /etc/mythtv/mysql.txt.

If you *have* changed the mysql mythtv account's password, then you will have to update /etc/mythtv/mysql.txt.  Note: this is really not the preferred way to do things, and expect breakages when upgrading packages.

---

### Post by arnabbiswas on 2007-03-09
Thanks superm1.

Actually I rebooted my box a couple of times and installed a few other apps (TVTime, Skype) and now this problem has gone away and I am able to launch mythtv-setup successfully as the mythtv user.

I however have to run "xhost +" as the original user before the su to mythtv, otherwise I still get the "cannot connect to X server" error. Is there a setting in any config file that I can change so that I do not have to run "xhost +" all the time?

And I am sorry that I am not able to provide further insights into what fixed the problem for me, but I am glad that I am able to get mythtv-setup to launch. Getting closer...

---

### Post by easyease on 2007-03-09
have you not tried kaffeine-xine from the repo's to watch tv on your pc? it takes like ten mins to set up and it works.

---

### Post by arnabbiswas on 2007-03-09
I will be, as a stop-gap to mythtv. Kaffeine-xine probably doesnt do the dvr stuff but at least u get basic tv viewing functionality.

---

### Post by superm1 on 2007-03-09
> **arnabbiswas said:**
> Thanks superm1.

Actually I rebooted my box a couple of times and installed a few other apps (TVTime, Skype) and now this problem has gone away and I am able to launch mythtv-setup successfully as the mythtv user.

I however have to run "xhost +" as the original user before the su to mythtv, otherwise I still get the "cannot connect to X server" error. Is there a setting in any config file that I can change so that I do not have to run "xhost +" all the time?

And I am sorry that I am not able to provide further insights into what fixed the problem for me, but I am glad that I am able to get mythtv-setup to launch. Getting closer...
Well to let you know, once you are in the mythtv group and have logged in/out once, it isn't necessary to "su mythtv" before launching mythtv-setup or anything.  Being in the mythtv group gives you the same permissions as launching as the mythtv user.

---

### Post by arnabbiswas on 2007-03-09
Thanks again superm1. Then I will not be logging in as mythtv anymore to run the mythtv-setup or to launch mythtv backend and frontend

---

