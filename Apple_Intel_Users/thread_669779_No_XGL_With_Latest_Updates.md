---
title: "No XGL With Latest Updates"
date: 2008-01-16
forum: Apple Intel Users
---

### Post by cworley420 on 2008-01-16
Recent updates appear to have broken my beryl effects.  Basically if i try to enable them from the appearence dialog it says they cannot be enabled.  Also, mysql has not been starting.  mysql might be a lock file issue where it was not shutdown properley.

snipptes from logs


----------- Xorg.log   START
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
----------- END

----------- debug (mysql issue) START
Jan 16 18:37:03 localhost /etc/init.d/mysql[7800]: 
Jan 16 18:37:51 localhost /etc/init.d/mysql[8578]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan 16 18:37:51 localhost /etc/init.d/mysql[8578]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan 16 18:37:51 localhost /etc/init.d/mysql[8578]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan 16 18:37:51 localhost /etc/init.d/mysql[8578]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan 16 18:37:51 localhost /etc/init.d/mysql[8578]: ----------- END

----------- syslog (mysql issue)START
Jan 16 18:37:36 localhost mysqld_safe[8283]: Please consult the MySQL manual section: 'Problems running mysql_install_db',
Jan 16 18:37:36 localhost mysqld_safe[8283]: and the manual section that describes problems on your OS.
Jan 16 18:37:36 localhost mysqld_safe[8283]: Another information source is the MySQL email archive.
Jan 16 18:37:36 localhost mysqld_safe[8283]: Please check all of the above before mailing us!
Jan 16 18:37:36 localhost mysqld_safe[8283]: And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
Jan 16 18:37:36 localhost mysqld_safe[8313]: 080116 18:37:36 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8313]: 080116 18:37:36 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8313]: ERROR: 1033  Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8313]: 080116 18:37:36 [ERROR] Aborting
Jan 16 18:37:36 localhost mysqld_safe[8313]: 
Jan 16 18:37:36 localhost mysqld_safe[8313]: 080116 18:37:36 [Note] /usr/sbin/mysqld: Shutdown complete
Jan 16 18:37:36 localhost mysqld_safe[8313]: 
Jan 16 18:37:36 localhost mysqld_safe[8323]: 080116 18:37:36 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8323]: 080116 18:37:36 [ERROR] /usr/sbin/mysqld: Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8323]: ERROR: 1033  Incorrect information in file: './mysql/user.frm'
Jan 16 18:37:36 localhost mysqld_safe[8323]: 080116 18:37:36 [ERROR] Aborting
----------- END

Can someone help me find the problem.

Intel PowerBook
ATI (not sure where to find the specific information)
kernel 2.6.17-10-386

-chris worley

---

### Post by cworley420 on 2008-01-16
Actually i was running 2.6.22 but, after the update wirless and sound broke as well.  So, I went to the previous kernel and they worked.  I am going to go back to 2.6.22 and see what I can do.

-chris worley

---

### Post by cworley420 on 2008-01-16
In the synaptic history i found some stuff was removed.  I went in and assured that some of the headers and other stuff were installed.  Here is a list of what i had to reinstall and for somereason was removed during updates a few weeks ago.

Alot of this is some postgres stuff i installed.  but, i had to add the linux-image and linux-headers stuff back.   now my sound, wireless and xgl works


Installed the following packages:
atlas3-base (3.6.0-20.6)
gcc-3.4-base (3.4.6-6ubuntu2)
libg2c0 (1:3.4.6-6ubuntu2)
libgfortran2 (4.2.1-5ubuntu4)
libpg-java (8.2-504-1)
libpg-perl (1:2.1.1-3)
libpgsql-ruby (0.7.1-10)
libpgsql-ruby1.8 (0.7.1-10)
libpq4 (8.1.10-1)
linux-headers-2.6.22-14-server (2.6.22-14.47)
linux-headers-386 (2.6.22.14.21)
linux-image (2.6.22.14.21)
linux-image-386 (2.6.22.14.21)
linux-source-2.6.22 (2.6.22-14.47)
linux-ubuntu-modules-2.6.22-14-386 (2.6.22-14.37)
mysql-admin (1.2.5rc-2ubuntu3)
mysql-admin-common (1.2.5rc-2ubuntu3)
mysql-client (5.0.45-1ubuntu3.1)
mysql-doc-5.0 (5.0-0ubuntu1)
mysql-query-browser (1.2.5beta-3ubuntu6)
mysql-query-browser-common (1.2.5beta-3ubuntu6)
pgadmin3 (1.4.3-2.1ubuntu1)
pgadmin3-data (1.4.3-2.1ubuntu1)
pgagent (1.4.3-2.1ubuntu1)
php5-pgsql (5.2.3-1ubuntu6.3)
phppgadmin (4.1.2-1)
postgresql (8.2.6-0ubuntu0.7.10.1)
postgresql-8.1 (8.1.10-1)
postgresql-8.1-pljava-gcj (1.3.0-1ubuntu2)
postgresql-8.2 (8.2.6-0ubuntu0.7.10.1)
postgresql-8.2-plr (1:8.2.0.1-2)
postgresql-8.2-plruby (0.5.0-2)
postgresql-8.2-plsh (1.2-2)
postgresql-client (8.2.6-0ubuntu0.7.10.1)
postgresql-client-8.1 (8.1.10-1)
postgresql-client-8.2 (8.2.6-0ubuntu0.7.10.1)
postgresql-client-common (78)
postgresql-common (78)
postgresql-contrib-8.2 (8.2.6-0ubuntu0.7.10.1)
postgresql-plperl-8.2 (8.2.6-0ubuntu0.7.10.1)
postgresql-plpython-8.2 (8.2.6-0ubuntu0.7.10.1)
python-egenix-mxdatetime (3.0.0-2ubuntu1)
python-egenix-mxtools (3.0.0-2ubuntu1)
python-pygresql (1:3.8.1-2)
r-base-core (2.5.1-1)
wwwconfig-common (0.0.48)

---

### Post by cyberdork33 on 2008-01-17
you have to have ati drivers linked to the kernel you are using. if you upgrade the kernel, modules that are linked to the kernel will break until you reinstall them. That first xorg log looks like you xorg.conf might be messed up as it is trying to access a wacom tablet.

---

