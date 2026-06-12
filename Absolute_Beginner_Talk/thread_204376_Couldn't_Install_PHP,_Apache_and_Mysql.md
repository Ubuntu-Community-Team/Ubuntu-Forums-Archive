---
title: "Couldn't Install PHP, Apache and Mysql"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-26
I did this

```


avinash@avinash:~$ sudo aptitude install apache2
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Note: selecting "apache2-mpm-worker" instead of the
      virtual package "apache2"
The following NEW packages will be automatically installed:
  apache2-common apache2-utils libapr0 libpcre3 openssl ssl-cert
The following NEW packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0 libpcre3 openssl
  ssl-cert
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2273kB of archives. After unpacking 6853kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)' in the drive '/cdrom/' and press enter

W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package openssl.
(Reading database ... 56661 files and directories currently installed.)
Unpacking openssl (from .../openssl_0.9.7g-1ubuntu1_i386.deb) ...
Creating directory /etc/ssl
Selecting previously deselected package ssl-cert.
Unpacking ssl-cert (from .../ssl-cert_1.0-11_all.deb) ...
Selecting previously deselected package libpcre3.
Unpacking libpcre3 (from .../libpcre3_5.0-1.1ubuntu2_i386.deb) ...
Selecting previously deselected package libapr0.
Unpacking libapr0 (from .../libapr0_2.0.54-5ubuntu2_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.0.54-5ubuntu2_i386.deb) ...
Selecting previously deselected package apache2-common.
Unpacking apache2-common (from .../apache2-common_2.0.54-5ubuntu2_i386.deb) ...
Selecting previously deselected package apache2-mpm-worker.
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.0.54-5ubuntu2_i386.deb) ...
Setting up openssl (0.9.7g-1ubuntu1) ...

Setting up ssl-cert (1.0-11) ...

Setting up libpcre3 (5.0-1.1ubuntu2) ...

Setting up libapr0 (2.0.54-5ubuntu2) ...

Setting up apache2-utils (2.0.54-5ubuntu2) ...
Setting up apache2-common (2.0.54-5ubuntu2) ...
Setting Apache2 to Listen on port 80. If this is not desired, please edit /etc/apache2/ports.conf as desired. Note that the Port directive no longer works.
Module userdir installed; run /etc/init.d/apache2 force-reload to enable.

Setting up apache2-mpm-worker (2.0.54-5ubuntu2) ...
 * Starting web server (Apache2)...                                      [ ok ]

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No candidate version found for mysql-server
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ sudo aptitude install libapache2-mod-auth-mysql
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "libapache2-mod-auth-mysql"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ sudo aptitude install php5-mysql
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "php5-mysql"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ sudo aptitude install phpmyadmin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "phpmyadmin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ cd /usr
avinash@avinash:/usr$ sudo ./bin/mysql_install_db --user=mysql
sudo: ./bin/mysql_install_db: command not found
avinash@avinash:/usr$ sudo ./bin/mysql_install_db --user=mysql
sudo: ./bin/mysql_install_db: command not found
avinash@avinash:/usr$ sudo /bin/mysql_install_db --user=mysql
sudo: /bin/mysql_install_db: command not found
avinash@avinash:/usr$ ./bin/mysql_install_db --user=mysql
bash: ./bin/mysql_install_db: No such file or directory
avinash@avinash:/usr$ sudo mysql -u root
sudo: mysql: command not found
avinash@avinash:/usr$ cd
avinash@avinash:~$ sudo aptitude install mysql-admin
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "mysql-admin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
avinash@avinash:~$ cd /usr
[B]avinash@avinash:/usr$ sudo ./bin/mysql_install_db --user=mysql
sudo: ./bin/mysql_install_db: command not found
avinash@avinash:/usr$ sudo mysql -u root
sudo: mysql: command not found[/B]
avinash@avinash:/usr$



```

The bold thing is the error what i got. PLease see what mistake i did.

Here is my reference page.

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by Spleenie on 2006-06-26
I didn't read through ALL of the code there. but that error would suggest at the least that you don't have mysql-server installed.

type:

```
sudo apt-get install mysql-server libapache2-mod-auth-mysql php4-mysql
```

I am assuming you want php4. Change to php5-mysql above if you are or want to run php5

Also, I think your repositories may not be adequate, judging by the non-existent packages. try editing /etc/apt/sources.list and enabling universe if you havent already.

---

### Post by hardfire_avk on 2006-06-26
**sudo apt-get install mysql-server libapache2-mod-auth-mysql php4-mysql** Gave me this.

```


avinash@avinash:~$ sudo apt-get install mysql-server libapache2-mod-auth-mysql php4-mysql
Password:
Reading package lists... Done
Building dependency tree... Done
Package mysql-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package mysql-server has no installation candidate
avinash@avinash:~$


```

---

### Post by hardfire_avk on 2006-06-26
[QUOTE=Spleenie]
Also, I think your repositories may not be adequate, judging by the non-existent packages. try editing **/etc/apt/sources.list** and enabling universe if you havent already.[/QUOTE]

I don't know what to change in the **/etc/apt/sources.list**  file . So if it is same in all the OS then can u please show me one of it's right copy that i can change to.

---

### Post by Spleenie on 2006-06-26
[QUOTE=hardfire_avk]I don't know what to change in the **/etc/apt/sources.list**  file . So if it is same in all the OS then can u please show me one of it's right copy that i can change to.[/QUOTE]

Try going here:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Use this to get a good sources.list

---

### Post by hardfire_avk on 2006-06-26
[QUOTE=Spleenie]Try going here:

**[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)**

Use this to get a good sources.list[/QUOTE]
How do i use [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to get good sources. i couldn't do It. Really New to all this.

---

### Post by Spleenie on 2006-06-27
[QUOTE=hardfire_avk]How do i use [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to get good sources. i couldn't do It. Really New to all this.[/QUOTE]

First select your Ubuntu version, I will assume its Dapper (6.06) Then select your architecture, which will probably be i386 unless you are using 64 bit cpu

also type in your country code where asked (dont do if you are in US) and then check the two boxes after that

now lower down and to the right, there are more checkboxes. click the first 10 boxes you see going down. This will select those repositories described on the left of the page

That should be enough to go on with, now go to the very bottom, click the button that says "Give me a sources.list"

It will take you to a page that has a sources.list. highlight all the text on that page and type do <ctrl-c> to copy it.

now in a terminal do the following:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list
```

delete all the text and replace with the text you copied from the webpage. Save and then exit.

When a repository in this list has a GPG key, you need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)

```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

The KEYs are found on the repository page as GPG key. You may not need to do this, but it will stop aptget telling you the repositories aren't authenticated

now try 
```
sudo apt-get update
```

Now give those installations a go

Cheers

---

