---
title: "allow my sudo without password"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-12-07
i did:

```

EDITOR=gedit sudo visudo

```

uncommented the line
```

# Uncomment to allow members of group sudo to not need a password
%sudo ALL = NOPASSWD: ALL

```

now the file looks like:
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL = NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

changed my user group to root, but it still asks me for the password when i sudo... 
where did i go wrong and how to do what i want to?

---

### Post by jordanmthomas on 2007-12-07
You need to be in the group 'sudo', not 'root'.

---

### Post by shoaibi on 2007-12-07
> **jordanmthomas said:**
> You need to be in the group 'sudo', not 'root'.

i don't have any sudo group when i issue groups command...

---

### Post by jordanmthomas on 2007-12-07
Exactly, that's why you need to add yourself to it.  The line in sudoers file says that people in the sudo group (you're not in it) don't need a password.
Either that, or when editing your sudoers file change this:
```
# Uncomment to allow members of group sudo to not need a password
%[COLOR="Red"]sudo[/COLOR] ALL = NOPASSWD: ALL
```
to
```
%[COLOR="Red"]root[/COLOR] ALL = NOPASSWD: ALL
```

---

### Post by shoaibi on 2007-12-07
i  edited the file the way you said by replacing sudo with root, but it didn't work....

---

### Post by jordanmthomas on 2007-12-07
What groups *are* you in?

Put yourself in the sudo group and change that line back to sudo (you don't really want to be in root's group).
```
sudo gpasswd -a $USER sudo
```

---

### Post by shoaibi on 2007-12-07
Here is something that may interest you:
There are more then one groups with my name, though same gid, and:
```

shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ sudo gpasswd -a $USER sudo
Adding user shoaibi to group sudo
shoaibi@eagles-nest:~$ sudo -k
shoaibi@eagles-nest:~$ sudo fdisk -l
[sudo] password for shoaibi:

Disk /dev/hda:
####Some Information

shoaibi@eagles-nest:~$ sudo -k
shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ sudo -k
shoaibi@eagles-nest:~$ sudo fdisk -l
[sudo] password for shoaibi:

[1]+  Stopped                 sudo fdisk -l
shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ sudo gpasswd -a $USER sudo
[sudo] password for shoaibi:
Adding user shoaibi to group sudo
shoaibi@eagles-nest:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%sudo ALL = NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
shoaibi@eagles-nest:~$ sudo -k
shoaibi@eagles-nest:~$ sudo fdisk -l
[sudo] password for shoaibi:

[2]+  Stopped                 sudo fdisk -l
shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ 

```

---

### Post by jordanmthomas on 2007-12-07
Ok, Ubuntu seems to use admin as its group that can use sudo (and you are not being added to sudo for some reason).
Change the line in your sudoers file to use [COLOR="Red"]admin[/COLOR] instead of root or sudo and I believe you'll be golden.

Also, it is fine for you to be in several groups.

---

### Post by shoaibi on 2007-12-07
Well myself being in more then one group is not a problem, the problem is that in the System>Administration>Users and Groups > Manage Groups i see multiple groups with the same name and same gid

```

shoaibi@eagles-nest:~$ sudo -k
shoaibi@eagles-nest:~$ groups
shoaibi adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
shoaibi@eagles-nest:~$ sudo cat /etc/sudoers
[sudo] password for shoaibi:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
%admin ALL = NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by jordanmthomas on 2007-12-07
Well, for one thing you need to log out before your sudo will work like you want.
I am not familiar with the GUI for adding users, but your groups output looks fine so I would not worry too much about it,

---

### Post by shoaibi on 2007-12-07
Hmmmm, that's why....
Well i can't logout right now, have so much open, i will after a couple of hours and let you know :P :D

---

### Post by jordanmthomas on 2007-12-07
You can try it in one of your virtual terminals (ctrl - alt - f2)
log in there and see if it works right now.
You can return to X by pressing ctrl - alt - f7

---

### Post by shoaibi on 2007-12-07
nope, it didn't worked. i am not in sudo group, and to my surprise there is no sudo group to begin with. i am still in admin group, while admin according to the sudoers file need no password for sudo, but i do....

---

