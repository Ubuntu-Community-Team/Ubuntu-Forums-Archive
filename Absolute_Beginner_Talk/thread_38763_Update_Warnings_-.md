---
title: "Update Warnings -"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by Weta on 2005-06-01
Hello


Just bought a new PC with Ubuntu only installed on it.  So far enjoying the new system and community.  

The little logo on top of my screen tells me that there are 26 Ubuntu updates available.   I have two questions about updates:  

1.  When I activate Update Manager it tells me:   "W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)"  Can someone tell me what to do about this warning?

2.  Clicking "OK" to the above warning then prompts "Warning  You are about to install software that cannot be authenticated..... "  Sounds serious!  The warning applies to all 26 updates.  Can I safely hit the "Apply" button to install some or all of these?


Thanks


Weta

---

### Post by Kyral on 2005-06-01
No.1: No clue

No.2: YES!!

---

### Post by benplaut on 2005-06-01
1: backports changed their address... but not sure what it is (having the same problem)

2: it's like with Internet Explorer, in Windows, when you download a file, it tells all these dire warnings that it might harm your computer

---

### Post by NewbieNik on 2005-06-02
use terminal to edit your apt sources file and change the mirrormax.com address to ubuntuforums.org.

"sudo gedit /etc/apt/sources.list"

The changed line should then read:-

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

or remove it all together!!!

read "How to add repositories" in the ubuntu user guide. you'll find huge amounts of helpful stuff in there!

Beware of changing your apt sources list. make a backup of it first. If it goes pear-shaped you then have the original to replace.

---

### Post by g33k on 2005-06-02
[QUOTE=NewbieNik]use terminal to edit your apt sources file and change the mirrormax.com address to ubuntuforums.org.

"sudo gedit /etc/apt/sources.list"

The changed line should then read:-

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted[/QUOTE]


The problem I'm seeing is "401: Authorization Required"...Any ideas???

---

### Post by Gustav on 2005-06-02
[QUOTE=NewbieNik]use terminal to edit your apt sources file and change the mirrormax.com address to ubuntuforums.org.

"sudo gedit /etc/apt/sources.list"

The changed line should then read:-

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

or remove it all together!!!

read "How to add repositories" in the ubuntu user guide. you'll find huge amounts of helpful stuff in there!

Beware of changing your apt sources list. make a backup of it first. If it goes pear-shaped you then have the original to replace.[/QUOTE]
 USE THE MIRRORMAX MIRROR

it's not recommended to use the ubuntuforums mirror right now.

The warnings will be fixed in maybe a week or so according to the backport straff, but you don't have to care about them for now.

---

### Post by fng on 2005-06-02
edit /etc/apt/sources.list
```
$ sudo nano /etc/apt/sources.list
```
Look for the ubuntu backports lines and change them into this
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Update your apt and upgrade the programs
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

---

### Post by NewbieNik on 2005-06-02
[QUOTE=fng]edit /etc/apt/sources.list
```
$ sudo nano /etc/apt/sources.list
```
Look for the ubuntu backports lines and change them into this
```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```
Update your apt and upgrade the programs
```
$ sudo apt-get update
$ sudo apt-get upgrade
```[/QUOTE]
 I bow to fng's superior knowledge. You are 100% correct with the repositories and I apologise to weta and g33K for any confusion caused!

---

### Post by Weta on 2005-06-02
Hello

Thank you all for your help.  I installed the updates last night, which went flawlessly.  I will give the warning about the backports mirror a little while to resolve itself (but have kept a copy of your advice what to do if this doesn't happen).

---

