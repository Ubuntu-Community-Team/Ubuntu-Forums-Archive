---
title: "Apt get trouble"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by AdrianOC on 2006-08-20
Hi all,

Could someone please correct this command for me, Im starting to play with ubuntu + linux and Im in the process of going through a guide. Ive gotten stuck on this one step and I cant seem to figure it out.

Basicaly the guide asked me to type the following

```
# apt-get install php4 php4-gd php4-cgi php4-mysql libapache2-mod-php4 php4-pear php4-ldap php4-snmp
```

But it didnt like it at all, and threw up something about php4. So I googled a bit and found their was a Php5, so I replaced all the php4 with php5 but then it threw up errors about "php5-pear" not being in existance. Now I cant seem to get past this piece googled pear and php but I cant seem to find anything relevant.

Any ideas?
(Sorry I dont have the actual code/error, posting from a different PC) Thanks

---

### Post by scxtt on 2006-08-20
most likely a problem w/ your /etc/apt/sources.list (i.e. you need to enable the right repos) ... this is what mine looks like, and what i get when i search for "pear":
```
:> aptitude search pear
Password:
p   pearpc                                              - PowerPC architecture emulator
p   php-pear                                            - PEAR - PHP Extension and Application Repository
p   php4-pear                                           - PHP Extension and Application Repository (transitional package
p   php4-pear-log                                       - Log module for PEAR

:> cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by AdrianOC on 2006-08-21
Thanks scxtt,

Ill try that and see what happens

---

### Post by rowanparker on 2006-08-21
For more info on installing webserver like things look [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

