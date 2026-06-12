---
title: "can't install anything?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-18
I can't install anything using "Add/Remove Applications" or "Synaptic Package Manager".    
They were working fine yesterday but today everytime I try to install anything I get:

dpkg: syntax error: unknown user 'amavis' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

I don't know what the heck "amavis" is and how it got to be a user.  Please help.  Thanks

---

### Post by nightwolf2k5 on 2007-03-18
try typing
```
sudo apt-get -f install
```
in ur terminal..

but.. i dunno much.. its what i do whenever some error comes up with packages..

---

### Post by jtx472 on 2007-03-18
Thanks for the reply but that didn't work.

---

### Post by meborc on 2007-03-18
do you get the same error while doing ```
sudo apt-get update
```?
or just when you try to install something?

---

### Post by jtx472 on 2007-03-18
No.  I get a whole bunch of updates.

---

### Post by meborc on 2007-03-18
and if you try to install something, for example ```
sudo apt-get install nethack
```do you get the same error still?

---

### Post by jtx472 on 2007-03-18
I get this:

jtx472@Northgate:~$ sudo apt-get install nethack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nethack is a virtual package provided by:
  nethack-x11 3.4.3-8ubuntu3
  nethack-qt 3.4.3-8ubuntu3
  nethack-lisp 3.4.3-8ubuntu3
  nethack-gnome 3.4.3-8ubuntu3
  nethack-console 3.4.3-8ubuntu3
You should explicitly select one to install.
E: Package nethack has no installation candidate
jtx472@Northgate:~$

---

### Post by meborc on 2007-03-18
ahh... sry.. :) just try ```
sudo apt-get install nethack-console
```... i just gave you a package name that didn't exist :)
EDIT: just change nethack-console to the package you want to install... and if you get any errors report back

---

### Post by jtx472 on 2007-03-18
I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nethack-common
The following NEW packages will be installed:
  nethack-common nethack-console
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1285kB of archives.
After unpacking 3191kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe nethack-common 3.4.3-8ubuntu3 [454kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe nethack-console 3.4.3-8ubuntu3 [831kB]
Fetched 1285kB in 10s (125kB/s)                                                
Preconfiguring packages ...
dpkg: syntax error: unknown user `amavis' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)
jtx472@Northgate:~$

---

### Post by david_kt on 2007-03-18
Just try this command:

[INDENT]sudo apt-get update[/INDENT]

and then followed by:

[INDENT]sudo apt-get upgrade[/INDENT]

Answer yes for all question, and make sure it do not have error. If it has error while running those two commands, just repeat it again until you are successfully update and upgrade your system. After that, try again to install the program you wanted to install.

Regards,
DK

---

### Post by jtx472 on 2007-03-18
That didn't work either but thanks for all your efforts.  I think I'll give it a break till later.

---

### Post by jtx472 on 2007-03-18
cancel

---

