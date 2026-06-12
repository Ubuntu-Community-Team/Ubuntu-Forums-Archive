---
title: "Root password?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Foudre on 2006-09-08
I've used SuSE for a while now decided to try Ubuntu it works great with my hard ware suse was having troubles with, ie my monitor. Any ways when i installed it, it never prompted me for a root password.... It asked me to create one user and a pass for them. So i'm wanting to know what the defualt root password is, so i can change it, i found a way around what i was trying to do, but for future needs, like in a few hours when i install my xine and libraries for it, i'll be needing a pass i think, hmm, does ubuntu let you use rpms? If not i may need to also find my libs else how, or at least an equivilent for it, so i can watch dvds and avi. Sorry i rant some. But yes could some one tell me if there is a defualt root pass, and if so what it is.

---

### Post by infoburner on 2006-09-08
in ubuntu there is no root password by default. you use sudo from a user account that is in the "admin" group. your first user account is automatically in the admin account. for example:
```

sudo apt-get install xine

```
will download and install xine for you. it will ask you for your password. with sudo you use your own password, not the root password.

almost everything you want to do in ubuntu can be done with sudo, ive only had to set a root password once in a year of using ubuntu. if you really need to set the root password just do 
```

sudo passwd

```

as far as using rpms: you can use them, but you have to convert them from rpm to deb with alien. you will probably be able to find what youre looking for in the ubuntu repository anyway. open up synaptic

System->Administration->Synaptic Package Manager

and click the "Search" button, and type in what you are looking for. then double click what you want, and click apply. synaptic will download the program and libraries you need and install them for you.

post back here if you have questions

---

### Post by TyphoonJoe on 2006-09-08
Ubuntu is built so you should not "need" to log in as root for anything.  The philosophy is that it is safer to only be root when needed.    

If you want to have root privileges for command line there are many ways, here are 3:
```
sudo su -
```
```
sudo bash
```
```
sudo ksh
```

Also, you should run gksudo rather than sudo to run graphical apps with root privileges. 
```
gksudo gedit
```

Also though infoburner showed you have to set the root password... I'd suggest never logging in graphically as root, but its your box :)

---

### Post by aysiu on 2006-09-08
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by infoburner on 2006-09-08
> **TyphoonJoe said:**
> 
Also though infoburner showed you have to set the root password... I'd suggest never logging in graphically as root, but its your box :)

the only reason i did it that one time was that i was compiling/installing a package which did "su" somewhere in the install script. it was easier to temporarily to set the root passwd than it was to edit the install script. but typhoon is right :). dont do it

---

### Post by danielfretto on 2006-09-08
sorry to piggy back this thread but i'm getting no new replies on a similar thread i started yest.

i get a prompt for a password when i try these methods for gaining root access.  i did originally have passwords set up for user and root.  since i changed this option for convenience sake i've been unable to access synaptic or manual installs thru terminal.  i keep getting password prompts.

d@shedd:~$ sudo bash
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:

any suggestions?

---

### Post by aysiu on 2006-09-08
Are you entering your user password or your root password? As long as you belong to the *admin* group, you should be able to enter your user password.

If you're not sure if you belong to the admin group or not, type ```
groups
``` to find out.

If you need to add yourself to the *admin* group, try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by danielfretto on 2006-09-08
i've tried both user password and root password with no luck.

my user acct is d

here is what happened in the term:

d@shedd:~$ groups
d adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
d@shedd:~$

---

### Post by danielfretto on 2006-09-08
it seems as though i can't gain root access at all.

d@shedd:~$ root -i
bash: root: command not found
d@shedd:~$ sudo -i
Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts
d@shedd:~$ sudo adduser d admin
Password:

---

### Post by aysiu on 2006-09-08
Well, you're in the *admin* group. Can you check that your /etc/sudoers file is the same as this? ```
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

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` You'll have to boot into recovery mode to do this, as you apparently can't *sudo* in to see the file.

Full instructions here:
[http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)

---

### Post by danielfretto on 2006-09-08
d@shedd:~$ /etc/sudoers
bash: /etc/sudoers: Permission denied
d@shedd:~$

---

### Post by aysiu on 2006-09-08
Please read the link I posted earlier. You're not supposed to type ```
/etc/sudoers
```

---

### Post by danielfretto on 2006-09-08
sorry for delay.  this forum loads really slowly at times.

here's what i got.:confused: 

d@shedd:~$ /etc/sudoers
bash: /etc/sudoers: Permission denied
d@shedd:~$

---

### Post by danielfretto on 2006-09-08
now i think i see what you mean.

when i restart in recovery i don't get a password propt. 

i am prompted to hit Ctrl D.

when i do, the system boots reletively normally.  initially different in that it runs a bunch of script against an all black screen but then a normal desktop appears.

i don't think it's booting right.  :( 

i never do get a recovery screen to type commands the way your link instructs.

---

