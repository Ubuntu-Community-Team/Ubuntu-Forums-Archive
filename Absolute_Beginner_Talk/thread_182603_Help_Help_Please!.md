---
title: "Help Help Please!"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-26
TRying to install software/apps by using the Synaptic Manager but i get the same error no matter what u select somethiong about mediamate

any fix or suggestion guys?](*,)

---

### Post by bruce89 on 2006-05-26
Is this for anything?  Also do not double post!

---

### Post by empthollow on 2006-05-26
i am not familiar with that particular error, but most of my apt-get/synaptic errors are usually fixed with this command.  go to 
applications -> accesories -> terminal
and type
```
sudo apt-get -f install
```

---

### Post by meng on 2006-05-26
I don't know the answer, but it seems that the computer is trying to execute a "chown -R : [etc]" and getting back a syntax error. I don't usually bother looking at terminal output during installation, so this is new to me. But out of interest, what are the current ownership and permissions on /var/lib/mediamate/modules?

EDIT: forgive me for pointing out the fricking obvious.

---

### Post by edwardzafra on 2006-05-26
vlad@Appoloin:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mediamate (0.9.3.6-2) ...
+ set -e
+ MMVERSION=0.9.3.6
+ . /usr/share/debconf/confmodule
++ '[' '!' '' ']'
++ PERL_DL_NONLAZY=1
++ export PERL_DL_NONLAZY
++ exec /usr/share/debconf/frontend /var/lib/dpkg/info/mediamate.postinst config ure ''
+ set -e
+ MMVERSION=0.9.3.6
+ . /usr/share/debconf/confmodule
++ '[' '!' 1 ']'
++ '[' -z '' ']'
++ exec
++ DEBCONF_REDIR=1
++ export DEBCONF_REDIR
+ case "$1" in
+ db_get mediamate/webserver_type
+ _db_cmd 'GET mediamate/webserver_type'
+ echo 'GET mediamate/webserver_type'
+ IFS='
'
+ read -r _db_internal_line
+ RET=Apache
+ return 0
+ webtype=Apache
+ case $webtype in
+ servers=apache
+ chmod 640 /etc/mediamate/db.inc
+ db_get mediamate/mysql/configure
+ _db_cmd 'GET mediamate/mysql/configure'
+ echo 'GET mediamate/mysql/configure'
+ IFS='
'
+ read -r _db_internal_line
+ RET=yes
+ return 0
+ '[' yes = true ']'
+ . /usr/share/wwwconfig-common/php-extensions.sh
++ . /usr/share/wwwconfig-common/php.get
+++ for A in php3 php4
++++ echo php3
++++ sed -e 's|4||g;'
+++ B=php3
+++ I=/etc/php3/apache/php3.ini
+++ '[' -f /etc/php3/apache/php3.ini ']'
+++ for A in php3 php4
++++ echo php4
++++ sed -e 's|4||g;'
+++ B=php
+++ I=/etc/php4/apache/php.ini
+++ '[' -f /etc/php4/apache/php.ini ']'
+++ phpver=php4
+++ phpini=/etc/php4/apache/php.ini
+++ phpini=/etc/php4/apache/php.ini
++ '[' -f /etc/php4/apache/php.ini ']'
+ for server in '$servers'
+ '[' apache == apache2 ']'
+ '[' -d /etc/apache ']'
+ . /usr/share/wwwconfig-common/apache-run.get
++ '[' -z '' ']'
++ . /usr/share/wwwconfig-common/apache.func
+++ set -e
++ getwwwoption User /etc/apache/httpd.conf
++ getwwwoption=
++ '[' -f /etc/apache/httpd.conf ']'
+++ echo ''
+++ sed -e q
++ webuser=
++ getwwwoption Group /etc/apache/httpd.conf
++ getwwwoption=
++ '[' -f /etc/apache/httpd.conf ']'
+++ echo ''
+++ sed -e q
++ webgroup=
++ apache_run_get=done
+ chown -R : /var/lib/mediamate/modules
chown: `:': cannot omit both user and group
dpkg: error processing mediamate (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mediamate
E: Sub-process /usr/bin/dpkg returned an error code (1)
vlad@Appoloin:~$

this mean anything?

---

### Post by cskeide on 2006-05-26
[QUOTE=meng]I don't know the answer, but it seems that the computer is trying to execute a "chown -R : [etc]" and getting back a syntax error. I don't usually bother looking at terminal output during installation, so this is new to me. But out of interest, what are the current ownership and permissions on /var/lib/mediamate/modules?

EDIT: forgive me for pointing out the fricking obvious.[/QUOTE]
It's not that obvious... :) Seems to me like the package "mediamate" has a post-installation script that tries to fetch webuser and webgroup from /etc/apache/httpd.conf but fails in the process.

edwardzafra, check if /etc/apache/httpd.conf exists, and includes Group varible:```
cat /etc/apache/httpd.conf | grep Group
```

---

### Post by edwardzafra on 2006-05-26
how do i check this?

---

### Post by popkid on 2006-05-26
Looking at the output in the terminal posted, it looks like mediamate is trying to change ownership of a file to a user group combination with variables $webuser/$webgroup and these do not exist on the machine (looks like it is trying to grab them from /etc/apache/httpd.conf) so it is executing a chown command with no user/group...

Do you have apache installed?

pK.

EDIT: Ha, posted this and all the other replies popped up, your way ahead of me.... gl

---

### Post by popkid on 2006-05-26
[QUOTE=cskeide]It's not that obvious... :) Seems to me like the package "mediamate" has a post-installation script that tries to fetch webuser and webgroup from /etc/apache/httpd.conf but fails in the process.

edwardzafra, check if /etc/apache/httpd.conf exists, and includes Group varible:```
cat /etc/apache/httpd.conf | grep Group
```[/QUOTE]

like this, see post above yours...

cat /etc/apache/httpd.conf | grep Group

---

### Post by cskeide on 2006-05-26
[QUOTE=edwardzafra]how do i check this?[/QUOTE]
Open a terminal. (Applications -> Accessories -> Terminal)
Type the following:```
cat /etc/apache/httpd.conf | grep Group
```
This should return something like:
Group   wwwgroup

---

### Post by meng on 2006-05-26
First, I'm definitely not as smart as cskeide or popkid, so trust whatever they say over anything I say. But - here's a thought - do you really need to have mediamate installed? And if not, might uninstalling mediamate clear the way for installing all that other goodness first?

---

### Post by edwardzafra on 2006-05-26
just installed apache and it seems to fix it..thanx for the tip

---

### Post by cskeide on 2006-05-26
[QUOTE=meng]First, I'm definitely not as smart as cskeide or popkid, so trust whatever they say over anything I say. But - here's a thought - do you really need to have mediamate installed? And if not, might uninstalling mediamate clear the way for installing all that other goodness first?[/QUOTE]
Probably the smartest suggestion so far. ;)

---

### Post by meng on 2006-05-26
[QUOTE=edwardzafra]just installed apache and it seems to fix it..thanx for the tip[/QUOTE]
Wow that's great. Now who's going to let the mediamate folks know that they should fix their dependencies?

---

### Post by edwardzafra on 2006-05-26
lol meng i thing you just raise you hands on that

---

### Post by meng on 2006-05-26
[QUOTE=edwardzafra]lol meng i thing you just raise you hands on that[/QUOTE]
Actually it was a rhetorical question. The honor is all yours - contribute back to the community dude!

---

### Post by cskeide on 2006-05-26
[QUOTE=meng]Wow that's great. Now who's going to let the mediamate folks know that they should fix their dependencies?[/QUOTE]
It's fixed in dapper...
```
Package: mediamate
Version: 0.9.3.6-4
Section: universe/web
Maintainer: Jamin W. Collins <jcollins@asgardsrealm.net>
**Depends: httpd**, php4-mysql, php4, wwwconfig-common, libphp-adodb, debconf (>=
         0.5) | debconf-2.0

```

---

### Post by meng on 2006-05-26
[QUOTE=cskeide]It's fixed in dapper...
```
Package: mediamate
Version: 0.9.3.6-4
Section: universe/web
Maintainer: Jamin W. Collins <jcollins@asgardsrealm.net>
**Depends: httpd**, php4-mysql, php4, wwwconfig-common, libphp-adodb, debconf (>=
         0.5) | debconf-2.0

```[/QUOTE]
:oops: I should have checked first. Thanks for pointing this out.

---

### Post by redistributer on 2006-05-26
check to see if apache is even installed it looks like that might be the problem

---

