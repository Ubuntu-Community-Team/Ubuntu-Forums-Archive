---
title: "Oracle Database 10g Express Edition"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2005-11-02
I downloaded this Oracle version 
[http://www.oracle.com/technology/products/database/xe/index.html](http://www.oracle.com/technology/products/database/xe/index.html) for free... there is an installation for linux but it's RedHat based (rpm file)... i use alien to convert the rpm file to .deb (sudo alien oracle_xe_10.rpm) but when i install the deb file (sudo dpkg -i oracle-xe_10.2.0.1-1.1_i386.deb) it only extract the files and make no configuration... and i can't find how to configure that version for ubuntu/debian 

does anyone have a better way to install rpm files or deb files?  or maybe to cheat on the rmp file and pretend to be a redhat instead of an ubuntu... i don't know.. im just wondering who to make this work

thanks

---

### Post by pccampos on 2005-11-04
Hi,

I'm downloading the .rpm right now, if anyone has the answer for this, it would be appreciated.


Thanks

---

### Post by msinger1 on 2005-11-13
Hope this helps:  [https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g)

---

### Post by msinger1 on 2005-11-13
Ok so I'm trying to install Oracle as well and I'm using the wiki that I posted above ([https://wiki.ubuntu.com/Oracle10g)](https://wiki.ubuntu.com/Oracle10g)).

I'm getting a problem that says something like "TNS: Lost Contact" during the install.

Did anyone else have this problem?

Also in the wiki, it says in /etc/inittab to replace the following line:

h1:35:respawn:/etc/init.d/init.cssd run >/dev/null 2>&1 </dev/null

I don't have this line in my /etc/inittab file.

Finally, the wiki says:

"Next, you need to edit the script that oracle installs. Navigate to line 83 and replace it with this:"

It never refers to the script by name, however.  Which script is it talking about?

---

### Post by fluxx on 2005-11-19
Hi,

Converting the .rpm with alien to .deb left, in my case, out the 'seeddb' which should be in '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/config/seeddb'. You can use the ubuntu archive manager and extract the seeddb and copy it in place. Also oracle is missing a library, which was easy to find at rpmfind.org (sorry, forgot the name) and then put in '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib'. 

Basicaly you should do it by hand: create user oraclexe:dba, edit init.ora and initXETemp.ora, run the commands in '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/config/scripts/XE.sh and XE.sql ' step by step. Then copy 'oracle-xe' (same dir) to /etc/init.d/ and do some more editing -read the errors and correct this in 'oracle-xe'. 
So, where's the howto? I should do a clean install again and write down every step, but time has got me (I don't know where to find the time to do this again). I just want to let you know it is possible and, once installed, it works smooth... Beautifull little app, but knowing a bit oracle may help you.
Good luck,
Bert.

---

### Post by elmicha on 2005-11-19
I also installed Oracle XE just today and was missing the seeddb. Apparently the "/etc/init.d/oracle-xe configure" removes the seeddb - and I had done this configure step several times until I had all the pieces together. I downloaded the oracle-xe-10.2.0.1-0.1.i386.rpm and tried to convert it with alien. The resulting deb package threw everything in /usr/lib/oracle/xe and didn't run any scripts to configure the whole thing. I suspected that Ubuntu's alien was too old, so I installed the newest alien package from Debian (sorry, I don't have the URL anymore). 
```
dpkg -i alien_8.59_all.deb
``` 
Same problem as before - no scripts, no configuration. Finally I figured out that alien has a -c switch (if all else fails, read the manual...). ```
alien -c oracle-xe-10.2.0.1-0.1.i386.rpm
``` Then I started with the Oracle 10g wiki entry [https://wiki.ubuntu.com/Oracle10g](https://wiki.ubuntu.com/Oracle10g) - but only until before the *Installation* chapter. I also needed to install libaio (not sure whether the -dev is necessary). ```
apt-get install libaio-dev
dpkg -i oracle-xe_10.2.0.1-1.1_i386.deb
```
Now this prints a message that you need to run */etc/init.d/oracle-xe configure* - but please hold on a moment. Although the package is a .deb file, the directory structure is still for Redhat or SuSE. Some tiny fake scripts make oracle-xe work in Ubuntu. ```

mkdir /etc/sysconfig
echo '#! /bin/sh
logger -t $0 "called with args $*"' >/sbin/chkconfig
chmod +x /sbin/chkconfig
echo '
success () 
{
 echo " [OK]"
}
failure ()
{
  echo " [FAILED]" 
}' >/etc/init.d/functions
```
Now you could run the configure step - but I wanted to see any problems, and the oracle-xe script redirects everything to /dev/null. ```
sed -i 's|> */dev/null|## > /dev/null|' /etc/init.d/oracle-xe
``` Now everything should be prepared and we can run the configure: ```
/etc/init.d/oracle-xe configure
``` That should work, finally. You still need to set a few environment variables: ```

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH
```
You should also put these in /etc/bash/bash.rc (I'm not sure where we are supposed to add environment variables in Ubuntu - Gentoo has a nice /etc/env.d directory which has many files with the variables that are needed for all the different packages).

Now you should be able to use sqlplus. ```
sqlplus sys as sysdba
``` And the HTML-DB should be running and available at [http://127.0.0.1:8080/htmldb](http://127.0.0.1:8080/htmldb) (of course use the port number that you gave in the configure step). Oops, I forgot to mention that you should add the oracle-xe init script to your runlevels: ```
update-rc.d oracle-xe defaults
``` If you don't want to start Oracle on every boot, remove the /etc/rc*.d/S*oracle-xe links - but be sure to keep the K links so that oracle will be stopped correctly. Also, Oracle put some .desktop files in /usr/share/applications, all starting with "oraclexe". I couldn't find them in the menus (although I tried update-desktop-database). So I did: ```
cd /usr/share/applications
mkdir Oracle
mv oraclexe-* Oracle
``` and then dragged this folder to the desktop with Nautilus.

---

### Post by carlosble on 2005-12-01
Thanks for your help. I had installed Oracle XE following your steps and making some others. I didnt need extra Debian packages, it was sufficient with Ubuntu Breezy repositories. This is all I done:
```

alien -d --test  -c --verbose oracle-xe-10.2.0.1-0.1.i386.rpm
apt-get install libaio-dev
dpkg -i oracle-xe_10.2.0.1-1.1_i386.deb
mkdir /etc/sysconfig

```
Create file /etc/init.d/functions :
```

#!/bin/sh
success ()
{
 echo " [OK]"
}
failure ()
{
  echo " [FAILED]"
}

```
Create file /sbin/chkconfig:
```

#!/bin/sh
logger -t $0 "called with args $*"

```
Set x bit:
```

chmod +x /etc/init.d/functions
chmod +x /sbin/chkconfig

```
Other little hack:
```

touch /etc/redhat-release

```
Start configuration:
```

/etc/init.d/oracle-xe configure

```
Export environment variables: 
```

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH

```
(Add the lines above in .bashrc)

Creating database:
```

cp /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/dbs/init.ora /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/dbs/initXE.ora

```
Edit initXE.ora and put database name and the pool size:
```

db_name=XE
shared_pool_size = 62198988

```

Then run this command fron bash:
```

sqlplus sys as sysdba

```
The password is the installation password

Start database inside sqlplus :
```

SQL> startup pfile=dbs/initXE.ora

```
This will give you some errors on control_files but never mind because it will be created with the next command:
```

SQL> create database XE;

```

Now I have some problems configuring database because the HTML DB application doesn't run, the only tool I found is sqlplus. And some basic objects like DBA are missing:
```

SQL> SELECT * FROM DBA;

```
(Statement above causes missing errors). 
I browse in oracle books and official documentation but nothing works in this Oracle XE (User_Users, DBA, System_Users...) 
Finally, I installed MaxDB for my purposes and delete Oracle 10g Express from my harddisk :(

---

### Post by lreyes6 on 2005-12-16
thanks 2 everybody in this post... i installed oracle over ubuntu and works great... 

Thanks Again!

---

### Post by mark_g on 2005-12-19
Thanks for the detailed instructions.
Oddly enough I can't start the sqlplus program. There seems to be a directory called /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/sqlplus/ , but no executable.
Any other way to do the last steps without sqlplus?

---

### Post by mark_g on 2005-12-19
Problem solved. Environment variables were configured incorrectly.

---

### Post by bavs on 2005-12-21
i have the same problem i cant start sqlplus
so how did you manage to set environment variables please :)

---

### Post by bavs on 2005-12-21
ok anyone available for help
atlast i got my oracle to work after like  2 nights without sleep
i can run sqlplus
now for the [http://localhost.localdomain:5500/em](http://localhost.localdomain:5500/em)
how can i find out my localhost and local domain? please help

---

### Post by mark_g on 2005-12-24
I just forgot to log out and then log in again, so the shell reads the .bashrc file again.
Of course you musn't forget to first add

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH

to the .bashrc file.

---

### Post by bavs on 2005-12-24
thank you all you guys and for the great wiki now oracle works like a dream :)
better and faster than windows xp as well

---

### Post by squidward on 2006-01-14
I just finished an Oracle 10g install.  It was a tremendous lift... as you may have guessed, nothing worked quite right the first time.

Actually, I first tried Oracle Express.  It was ornery.  I gave up and deleted it.  Then I tried the full version of 10g... ironically, it was easier to install than the Express.

I can't remember all the hacks I did, there were so many.  But I did use comments from this thread, plus:

[Oracle]("http://www.oracle.com/technology/tech/linux/install/index.html")
[Williams]("http://www.togaware.com/linux/survivor/Oracle_10g.shtml")
[Knaggs]("http://www.penlug.org/twiki/bin/view/Main/DebianSargeNetinstOracleInstall")

Some hacking I recall:  
[LIST]Do not use root (sudo) for any install procedures unless specifically told to do so.  The install is designed to be done from the Oracle Account... which is is not as empowered as root.  I did a step as root, that I should have done as Oracle and I ended with screwed up permissions.
[/LIST]
[LIST]The biggest problem was getting the TNSlistner to run right.  I poked around quite a bit and can't remember zactly what I did... but I do remember that the listener.ora built by the installer had a syntax error.  I never pin pointed the error, but I downloaded a known good file from the web and editted that to my needs.  Bingo, it worked.
[/LIST]
[LIST]Keep a log of what you did... I didn't as you can see.
[/LIST]
[LIST]Don't drink alcohol (until you're done).  You'll need your wits.
[/LIST]
[LIST]If this install is for Production... STOP.  Use Red Hat or Suse.  I luv UB, but it is my home box.  If lives/money/or a job were on the line, I'd go with a distro recognized by Oracle.  I suspect this install would have been about a 30 minute project with Red Hat or Suse.
[/LIST]Now I'm going to toy with Eclipse/Sun Studio/Jdeveloper and see which one I like to use best hitting the 10g.

Frankly, if my potential client didn't already have an under-used site license for Oracle, I'd probably would look at MySQL 5.0.

---

### Post by lamego on 2006-01-19
I am getting the following erro when trying to start the db, I have installed and configured as described above.

sudo /bin/su oraclexe -c '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/sqlplus -s /nolog @/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/config/scripts/startdb.sql'
ORA-00371: not enough shared pool memory, should be atleast 62198988 bytes

Any ideas ?

---

### Post by lnxpwr on 2006-01-23
lamego, your Init.ora parameter <shared_pool_size> is too small ...increase it !
greetinx

---

### Post by BrandNuUbantu on 2006-05-02
Hi there
When i try to run the following command from root, i am getting an error: "Couldn't find package libaio-dev". How do do i resolve this?

apt-get install libaio-dev

TIA
BNU

---

### Post by hibernatus on 2006-08-16
Hi,

i don't know if you have seem but there is a version for debian/ubuntu know available for free down load on [OTN]("http://www.oracle.com/technology/software/products/database/xe/htdocs/102xelinsoft.html")

Hibern

---

### Post by lamego on 2006-08-16
There is now an apt-get repository up on oss.oracle.com for XE. Just add:

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

to /etc/apt/sources.list and then:

# apt-get update
# apt-get install oracle-xe

---

### Post by relacksd on 2006-09-06
I have installed Oracle XE on Dapper using the repository at...

deb [http://oss.oracle.com/debian](http://oss.oracle.com/debian) unstable main non-free

...and all seems to have gone well except for one thing. That is, when I go to log in to SQLPlus from the command line, I cannot just enter...

sqlplus myuser

...but rather, I have to specify the ORACLE_SID in the command, like...

sqlplus myuser@xe

With the former I get the following...

ORA-01034: ORACLE not available
ORA-27123: unable to attach to shared memory segment
Linux Error: 13: Permission denied

...while the latter works perfectly.

In the other Oracle installations I've done (a while back on traditional UNIXes) I've never had to do this as long as the ORACLE_SID environmental variable was set right. Does anyone have any idea as to why this is different for me on Ubuntu?

Thanks for any help you can provide.

---

### Post by hibernatus on 2006-09-08
Hi,

you have the erreor :

ORA-01034: ORACLE not available
ORA-27123: unable to attach to shared memory segment
Linux Error: 13: Permission denied

is your DB and listener start? and are you renning you sqlplus commande as the oracle user?

i invite you to try to connect to your db with the following steps :

1 : verrify that your instance is start 


> ps -ef|grep pmon

is their is a *pmon* process this mean that your instance is start

2 : logon your system as the oracle user 

> su - oracle 

3 set your environement (if i remind correctly this could be done with a config file provided with the installation.
otherwise you can set up manually 
> set ORACLE_SID=....
set ORACLE_HOME=....

4 verify that your listener is started 

> lsnrctl status 

this could be done if your $ORACLE_HOME/bin is in your path

=> if the listener is start => ok
=> if the listener is not start => lsnrctl start (you MUST have environement variable before doing that)


5 you can connect with your sys user to verify the state of your instance 

> sqlplus / as sysdba 
select * from v$istance;
exit

this will return the information and the state of your ORACLEXE instance


then you willbe able to used your ORACLEXE instance

---

### Post by relacksd on 2006-09-12
> you have the erreor :

ORA-01034: ORACLE not available
ORA-27123: unable to attach to shared memory segment
Linux Error: 13: Permission denied

is your DB and listener start?

Yes. I have not had a problem logging in and using the database as long as I use the "sqlplus username@xe" format as opposed to the simpler "sqlplus username".

> and are you renning you sqlplus commande as the oracle user?

This turned out to be a very good suggestion. When I switch to the oracle user and run sqlplus I do not need to use the @xe portion of the command. That seems to mean that my having to use the @xe portion is most likely related to a permissions issue or environmental variable issue of some kind. Best I can tell, the latter looks to be correct, so I'll have to nose around with the permissions and see what I can find. This would be consistent with the error message, too.

I am trying to make it so that ordinary users can use sqlplus without needing to know that the instance name is xe--I will not let everyone log in as user oracle. So, I've got to find out where the permissions are off. If you've got any suggestions in this realm, I'd be most appreciative.

Thanks for your help. I feel like I'm a lot closer now.

---

### Post by clevershark on 2006-11-14
A quick question, to no one in particular -- has anyone managed to get the Oracle 10g Express .deb package to work in Edgy? I had it working fine in Dapper, but for some reason when I try installing in Edgy I can't even start the database. There's no error message -- the DBMS starts briefly, and immediately quits.

Maybe I should try installing in Dapper then upgrading to Edgy? The thing is that I need vmware to work also (I have the opposite problem there -- I can't get vmware installed in Dapper, but it works find in Edgy).

---

### Post by hibernatus on 2006-11-15
Hi,

Have you look in the alert log file? is their anny message in this file?

Regard

---

### Post by clevershark on 2006-11-16
After much tweaking I did manage to get the database core to work, but not application express... 

Frankly I don't think anyone has this working in Edgy, except perhaps by having installed it in Dapper and then upgraded (and even then I've not seen that claim explicitly made anywhere). I have a feeling that I could spend a week doing additional tweaks and maybe get things working, but frankly I don't have a week available and there's no guarantee that I can get everything to work anyway, so I'm giving up on Edgy (and vmware) until that's resolved.

---

### Post by arabxptyltd on 2006-11-22
I have just successfully installed under 6.10, but not without pain.

I installed, but when I tried APEX and sqlplus I could not login. Knowing I typed in the right password, I tried to uninstall, and that led to a world of pain as re-installs kept failing in multiple areas.

After finally sorting, and re-installing via apt-get instead of dpkg I have again hit the same problem.

I can get the APEX login screen, but my sys or system login is invalid, same with sqlplus.

---

### Post by troach on 2006-11-24
> **clevershark said:**
> After much tweaking I did manage to get the database core to work, but not application express... 

Frankly I don't think anyone has this working in Edgy, except perhaps by having installed it in Dapper and then upgraded (and even then I've not seen that claim explicitly made anywhere). I have a feeling that I could spend a week doing additional tweaks and maybe get things working, but frankly I don't have a week available and there's no guarantee that I can get everything to work anyway, so I'm giving up on Edgy (and vmware) until that's resolved.

I got Apex to start on the latest version of Ubuntu.

The listener is being refused permission to startup the Listener on the (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))

Line. Ubuntu did something in Edgy Eft to not allow processes to start up like they did. Something to do with the IPC protocol? Does anyone have any idea to give permissions so that the Listener can start with the IPC protocol? Once I commented out that line by doing this:

# (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))

The listener started up fine and I was able to connect via APEX by going to [http://127.0.0.1:8080/Apex](http://127.0.0.1:8080/Apex)

The IPC I think is going to mess you up because you won't be able to connect internally.

For example:

Connect / as sysdba;

---

### Post by fisherbln on 2006-12-17
I've gotten oracle to install on edgy with minimal problems. I didn't have to customize anything other than just apt-get'ing the install just like this guide: [https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)

I can connect via the 127.0.0.1:8080/apex webpage and run commands, create users, etc. However, when I run this command $ sqlplus sys as sysdba I get this result: 
```

SQL*Plus: Release 10.2.0.1.0 - Production on Sun Dec 17 10:06:29 2006

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Enter password: 
ERROR:
ORA-12154: TNS:could not resolve the connect identifier specified

```

Any ideas? I am an oracle n00b, so hopefully it's something stupid that I'm just missing.

---

### Post by hibernatus on 2006-12-18
Hi,

this message is usualy when your tnsname don't know the service name (or sid) you try to connect

if you do as oracle user :

lsnrctl status 

=> you should see your database regiserd 

you must have allso in your $ORACLE_HOME/network/admin/tnsname.ora
an antry corresponding to your database

can you allso try tnsping $ORACLE_SID

regard

---

### Post by fisherbln on 2006-12-18
> **hibernatus said:**
> Hi,

this message is usualy when your tnsname don't know the service name (or sid) you try to connect

if you do as oracle user :

lsnrctl status 

=> you should see your database regiserd 

you must have allso in your $ORACLE_HOME/network/admin/tnsname.ora
an antry corresponding to your database

can you allso try tnsping $ORACLE_SID

regard

```

$lsnrctl status
LSNRCTL for Linux: Version 10.2.0.1.0 - Production on 18-DEC-2006 11:31:26

Copyright (c) 1991, 2005, Oracle.  All rights reserved.

Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=my.host.com)(PORT=1521)))
STATUS of the LISTENER
------------------------
Alias                     LISTENER
Version                   TNSLSNR for Linux: Version 10.2.0.1.0 - Production
Start Date                17-DEC-2006 10:33:41
Uptime                    1 days 0 hr. 57 min. 44 sec
Trace Level               off
Security                  ON: Local OS Authentication
SNMP                      OFF
Default Service           XE
Listener Parameter File   /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/listener.ora
Listener Log File         /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
Listening Endpoints Summary...
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=my.host.com)(PORT=1521)))
  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=127.0.0.1)(PORT=8080))(Presentation=HTTP)(Session=RAW))
Services Summary...
Service "PLSExtProc" has 1 instance(s).
  Instance "PLSExtProc", status UNKNOWN, has 1 handler(s) for this service...
Service "XE" has 1 instance(s).
  Instance "XE", status READY, has 1 handler(s) for this service...
Service "XEXDB" has 1 instance(s).
  Instance "XE", status READY, has 1 handler(s) for this service...
Service "XE_XPT" has 1 instance(s).
  Instance "XE", status READY, has 1 handler(s) for this service...
The command completed successfully

```

```

$ tnsping XE

TNS Ping Utility for Linux: Version 10.2.0.1.0 - Production on 18-DEC-2006 11:33:15

Copyright (c) 1997, 2005, Oracle.  All rights reserved.

Used parameter files:
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin/sqlnet.ora


Used TNSNAMES adapter to resolve the alias
Attempting to contact (DESCRIPTION = (ADDRESS = (PROTOCOL = TCP)(HOST = my.host.com)(PORT = 1521)) (CONNECT_DATA = (SERVER = DEDICATED) (SERVICE_NAME = XE) (SID = XE)))
OK (10 msec)

```

I can login as the user HR, but whenever I try to use any other login, I get the ORA-12154: TNS:could not resolve the connect identifier specified error. If I use the wrong login/pass info, it says wrong login/pass, so I'm at a loss.

---

### Post by hibernatus on 2006-12-19
Hi,

When yo log in terminal as oracle.
Them you place your environement

> . oraenv

The answer to the question is your SID

then i invite you to connect in to your database as :

> sqlplus /nolog
connect / as sysdba
exit

Then if no error i invite you to try  with an other user (if you have created one)

> sqlplus /nolog
connect MY_USER/MY_PASSWD 
exit

---

### Post by troach on 2006-12-21
Give us the connect strings you are using. Copy and Paste it here. The one that works and the one that does not.

---

### Post by troach on 2006-12-21
> **troach said:**
> I got Apex to start on the latest version of Ubuntu.

The listener is being refused permission to startup the Listener on the (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))

Line. Ubuntu did something in Edgy Eft to not allow processes to start up like they did. Something to do with the IPC protocol? Does anyone have any idea to give permissions so that the Listener can start with the IPC protocol? Once I commented out that line by doing this:

# (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_FOR_XE)))

The listener started up fine and I was able to connect via APEX by going to [http://127.0.0.1:8080/Apex](http://127.0.0.1:8080/Apex)

The IPC I think is going to mess you up because you won't be able to connect internally.

For example:

Connect / as sysdba;


Fixed by doing this.

In my listener.ora I renamed this:

(DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC_F OR_XE)))

to this

(DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=IPCKEY)))

Then I issued this:

lsnrctl start

Then I logged into sqlplus like this:

sqlplus / as sysdba

and issued this

alter system register

Now try and connect to Application Express.

---

### Post by watermark1983 on 2007-08-09
I was installing Oracle Database10g
and i type the command  : sudo gedit /etc/bash/bashrc 
and add : 
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH 


but the erro message shows up : canot found the file.and canot save it.


where i could find the .bashrc  
and i searched some information.some tells to add the envirnoment variables in bash_profile.
and i dont understand the relationship between the bash_profile and bashrc...


  waiting for help online...............:)

---

### Post by SLIMwoogi on 2007-09-04
> **lreyes6 said:**
> I downloaded this Oracle version 
[http://www.oracle.com/technology/products/database/xe/index.html](http://www.oracle.com/technology/products/database/xe/index.html) for free... there is an installation for linux but it's RedHat based (rpm file)... i use alien to convert the rpm file to .deb (sudo alien oracle_xe_10.rpm) but when i install the deb file (sudo dpkg -i oracle-xe_10.2.0.1-1.1_i386.deb) it only extract the files and make no configuration... and i can't find how to configure that version for ubuntu/debian 

does anyone have a better way to install rpm files or deb files?  or maybe to cheat on the rmp file and pretend to be a redhat instead of an ubuntu... i don't know.. im just wondering who to make this work

thanks

Now you can download debian package from OTN.  
Download this debian package and run this command.

" sudo dpkg -i [the name of package you downloaded.]"

Good luck.!!!

---

### Post by robertrej on 2008-01-03
I installed oracle as well and it works fine l but how can set the server to Start' manually'
instead of  auto start.I believe when that server is running in the background it may slow
down my system some what.I do not always want oracle XE running.


                                                             thanks
                                                            bob

---

### Post by jjjjjj on 2008-05-10
The installer also needs 

apt-get install bc

---

