---
title: "Root User"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by cac007 on 2006-06-09
I type in su in the terminal, then it asks for the password.  I do not remember typing in a password in the installation.  Is there any way around this?

---

### Post by 23meg on 2006-06-09
The root user is disabled by default. You should prefer sudo.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-06-09
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) may help, also.

---

### Post by verbatim210 on 2006-06-09
[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

im trying to install xamp.

if i do su, i cant log in.. my password is "1"

if i do sudo, nothing happens.  how do i extract this 50meg file i just downloaded?

---

### Post by nanotube on 2006-06-09
[QUOTE=verbatim210][http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

im trying to install xamp.

if i do su, i cant log in.. my password is "1"

if i do sudo, nothing happens.  how do i extract this 50meg file i just downloaded?[/QUOTE]
so your user cannot use sudo? hmm. try going to the third link in my sig, and looking at the very first faq in the list.

---

### Post by verbatim210 on 2006-06-09
nano /etc/group

i get stuck here, wheres the admin group?

---

### Post by aysiu on 2006-06-09
[QUOTE=verbatim210]nano /etc/group

i get stuck here, wheres the admin group?[/QUOTE] Your /etc/group file should look like this: ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
**adm:x:4:verbatim**
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,verbatim
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,verbatim
floppy:x:25:haldaemon,verbatim
tape:x:26:
sudo:x:27:
audio:x:29:verbatim
dip:x:30:verbatim
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:verbatim
sasl:x:45:
plugdev:x:46:haldaemon,verbatim
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
crontab:x:104:
ssh:x:105:
lpadmin:x:106:verbatim
messagebus:x:107:
haldaemon:x:108:
slocate:x:109:
scanner:x:110:cupsys,verbatim
gdm:x:111:
verbatim:x:1000:
**admin:x:112:verbatim**
```

---

### Post by nanotube on 2006-06-09
[QUOTE=verbatim210]nano /etc/group

i get stuck here, wheres the admin group?[/QUOTE]
if your /etc/group does not look like what aysiu posted, (ie, there is no admin group or adm group) post your /etc/group file here, and we can take a look.

---

### Post by aysiu on 2006-06-09
You might also want to make sure that your /etc/sudoers file looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
```

---

### Post by verbatim210 on 2006-06-09
i went back to nano etc/group in attempt to get the screenshot.  now its empty.

i think i just killed my ubuntu, all i wanted to do was install xamp lol.  it cant be this much trouble, how is everyone else installing XAMP??

---

### Post by verbatim210 on 2006-06-09
sorry my newbie mistake.... i think i left out a "/"

  GNU nano 1.3.10             File: /etc/group

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon
floppy:x:25:haldaemon

---

### Post by aysiu on 2006-06-09
No, but it does look as if you have some groups missing there...

---

### Post by nanotube on 2006-06-09
[QUOTE=verbatim210]sorry my newbie mistake.... i think i left out a "/"

  GNU nano 1.3.10             File: /etc/group

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon
floppy:x:25:haldaemon[/QUOTE]

is this by any chance a server install?

---

### Post by verbatim210 on 2006-06-09
no its a text mode install from the alternate cd.  doesn't matter i just reformat the system it seems to be ok now.

just one question, when im in the terminal i am logged in as a user.  i read somewhere by default it disables ur root account or something.

well im trying to do some stuff that needs admin priviledges, how do i log into root?

i've tried this...
jo@four:~$ su
Password:
su: Authentication failure
Sorry.
jo@four:~$

i know i've entered the correct password coz wen i use sypnatic, i use the same password which im assuming is the root/admin password.

---

### Post by nanotube on 2006-06-10
[QUOTE=verbatim210]no its a text mode install from the alternate cd.  doesn't matter i just reformat the system it seems to be ok now.

just one question, when im in the terminal i am logged in as a user.  i read somewhere by default it disables ur root account or something.

well im trying to do some stuff that needs admin priviledges, how do i log into root?

i've tried this...
jo@four:~$ su
Password:
su: Authentication failure
Sorry.
jo@four:~$

i know i've entered the correct password coz wen i use sypnatic, i use the same password which im assuming is the root/admin password.[/QUOTE]

you should use "sudo" with your user password.
please check [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2006-06-10
*sudo* usually goes with a command. See the difference here: ```
jo@four:~$ su
Password:
root@four:~$ cp /etc/apt/sources.list /etc/apt/sources.list_backup
root@four:~$ exit
jo@four:~$
``` as opposed to ```
jo@four:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
jo@four:~$
```

---

