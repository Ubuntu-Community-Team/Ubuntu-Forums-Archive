---
title: "master password?"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by user on 2005-06-24
ok, here's my problem:
i've made a user account that has limited previllege and another one with an admin previllege. the mistake i've made is, i turned on the option to enable root login and then deleted the admin account. after some time, for some random reasons, i disabled root login and rebooted the computer (argg.. don't ask why)...
so now i only have one account that has ZERO admin previllege. so i can't install anything.... whenever i try to apt-get something, it prompts for a password, which i have no idea what it is. it's not the limited account's password since that account is not in sudoer's list, nor the "root" account password... 
thx in advance

---

### Post by intangible on 2005-06-24
Here ya go:

1. Boot from a Linux CD, get to a prompt, make sure to change to the root account (on a Ubuntu Live CD, that would be **sudo sh** to get to a root account.
2. **mkdir /mydrive**
3. **mount /dev/hda1 /mydrive** (where hda1 is your root partition)
4. **chroot /mydrive**
5. **passwd root** Enter the new root password
6. Log Out of everything, reboot and the root account will now have a password.

---

### Post by user on 2005-06-24
i tried to do that by ctrl-alt-f1 and changed the password
and didnt' work..

i have to do that from live cd?


if i do su root and type in the changed password, i can login to root
but if i just do apt-get w/o su'ing, i get a password prompt. so i type in the root password, and it doesn't work. :/

---

### Post by intangible on 2005-06-24
Yes, you'll want to boot from a live cd so you can use root on it to renable the root account on your Ubuntu.  After that, then you can log in as root to your regular system and add someone to the sudo file or add them to the admin group.

---

### Post by user on 2005-06-24
[QUOTE=intangible]Yes, you'll want to boot from a live cd so you can use root on it to renable the root account on your Ubuntu.  After that, then you can log in as root to your regular system and add someone to the sudo file or add them to the admin group.[/QUOTE]
 ok, so i guess that'll solve my root account problem.
but what's the reason that root password doesn't work when i try to apt-get from the limited account?

---

### Post by intangible on 2005-06-24
Just make sure you add the limited user to the "admin" group so sudo will work properly.

**adduser username admin**

---

### Post by user on 2005-06-24
[QUOTE=intangible]Just make sure you add the limited user to the "admin" group so sudo will work properly.

**adduser username admin**[/QUOTE]
 i added both admin and root to this limited user
but i still get a password prompt when i do stuff like trying to run login screen setup

if i do apt-get install gaim, i get
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

if i do sudo apt-get install gaim, i get a password prompt. i enter the changed root password, it says "sorry, try again"... :/

---

### Post by intangible on 2005-06-24
What does **/etc/sudoers** have in it?

It should have something like this near the bottom:
```

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=user]i added both admin and root to this limited user
but i still get a password prompt when i do stuff like trying to run login screen setup

if i do apt-get install gaim, i get
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

if i do sudo apt-get install gaim, i get a password prompt. i enter the changed root password, it says "sorry, try again"... :/[/QUOTE]
 If you run sudo, it asks for your - not root - password.

---

### Post by user on 2005-06-24
[QUOTE=intangible]Just make sure you add the limited user to the "admin" group so sudo will work properly.

**adduser username admin**[/QUOTE]
 i did both adduser username admin/root
still doesn't work

---

### Post by user on 2005-06-24
not root?
then...?

---

### Post by user on 2005-06-24
[QUOTE=intangible]What does **/etc/sudoers** have in it?

It should have something like this near the bottom:
```

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```[/QUOTE]


permission denied :/
both limited and root account

---

### Post by user on 2005-06-25
[QUOTE=user]permission denied :/
both limited and root account[/QUOTE]
 uhm.. any takes?

---

### Post by Alexander Kirillov on 2005-06-25
[QUOTE=user]uhm.. any takes?[/QUOTE]
 Please write exactly what you were typing - and what password you entered.

---

### Post by user on 2005-06-25
[QUOTE=Alexander Kirillov]Please write exactly what you were typing - and what password you entered.[/QUOTE]
 i typed 

/etc/sudoers

and got that permission denied messege
it didn't ask me for a password. just a simple denial :/

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=user]i typed 

/etc/sudoers

and got that permission denied messege
it didn't ask me for a password. just a simple denial :/[/QUOTE]
 If you want to edit a file, you should type 
<yourfavoriteeditorname> <filename>
not just <filename>
If this requires root privileges, do it  from root terminal or via sudo
E.g.: 
sudo gedit /etc/sudoers

---

### Post by user on 2005-06-26
[QUOTE=Alexander Kirillov]If you want to edit a file, you should type 
<yourfavoriteeditorname> <filename>
not just <filename>
If this requires root privileges, do it  from root terminal or via sudo
E.g.: 
sudo gedit /etc/sudoers[/QUOTE]
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

---

### Post by intangible on 2005-06-26
What does **groups username** (where username is the limited account) show?

---

### Post by user on 2005-06-26
[QUOTE=intangible]What does **groups username** (where username is the limited account) show?[/QUOTE]
 "limted" root dialout cdrom floppy audio dip video plugdev admin lpadmin scanner


another prob i have, 
chmod 777 /media/windows
doesnt work...
i can't change the folder permission

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=user]permission denied :/
both limited and root account[/QUOTE]


reboot....go into recovery mode.

at the prompt type this:

pico /etc/sudoers

add yourself to the file:

username ALL=(ALL) ALL

save it by hitting cntrl and "x" at the same time and reboot!

---

### Post by intangible on 2005-06-28
You have to change the mount options for the Windows drive, NTFS nor Fat32 will handle Linux file permissions.  Also, Write support for NTFS is experimental at best, so you might not want 777 for it anyway.  You may want to start a new thread for that question.  Check out [http://www.ubuntuguide.org](http://www.ubuntuguide.org) for some help accessing windows drives.

---

### Post by intangible on 2005-06-28
You would put the limted account's own password.  Sudo does not use the root password, but the limited account's password.

---

