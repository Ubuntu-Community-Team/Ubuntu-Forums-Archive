---
title: "sudo don't ask for passw"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by pcomelade on 2007-01-08
Hi all,

When I run a command with "sudo", it doesn't ask me for a password, but executes cleanly the command.
I'm using an account that has been already included in the group "admin" and "sudo". (Ubuntu Edgy 6.10, kernel 2.6.17-10-386)
What's going wrong?

Thanks in advance for your help

pcom

---

### Post by Bachstelze on 2007-01-08
Wait for 10 minutes, it will ask the password again ;)

---

### Post by scrooge_74 on 2007-01-08
usually you type sudo give your password and then sudo will remember it for about 15 minutes and will not ask it again during that time, maybe is that ?

---

### Post by pcomelade on 2007-01-08
I don't think so. I run "sudo -k" and the problems persists. When I reboot, the first "sudo" calls do the same thing (executes without asking a password).

Any idea?
Thanks for the help

M;

---

### Post by pcomelade on 2007-01-08
I'm posting you the output of "sudo cat /etc/sudoers" (again, no password required).

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


M;

---

### Post by tito2502 on 2007-01-08
Try resetting it with

sudo passwd

---

### Post by pcomelade on 2007-01-08
i've done the following:

$ sudo passwd
Enter new UNIX password: <new passwd entered>
Retype new UNIX password: <new passwd entered>
passwd: password updated successfully
$ sudo su

and again executes the sudo command without asking for a password!! :confused: 
when I type "su", I have to enter the password (the new one), but sudo executes without asking!!

Any other idea??
Thanks in advance!!

M;

---

### Post by steve.horsley on 2007-01-08
All very odd. Just as a quick check, look at my sudo file:
> steve@StevesPC:~$ which sudo
/usr/bin/sudo
steve@StevesPC:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 2 root root 91508 2006-10-09 12:37 /usr/bin/sudo
steve@StevesPC:~$ file /usr/bin/sudo
/usr/bin/sudo: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped


---

### Post by steve.horsley on 2007-01-08
> **pcomelade said:**
> i've done the following:

$ sudo passwd
Enter new UNIX password: <new passwd entered>
Retype new UNIX password: <new passwd entered>
passwd: password updated successfully
$ sudo su

and again executes the sudo command without asking for a password!! :confused: 
when I type "su", I have to enter the password (the new one), but sudo executes without asking!!

Any other idea??
Thanks in advance!!

M;
All you did there was set root's password (which you can now use with **su**).

---

### Post by moma on 2007-01-08
Write:
$ [COLOR="SeaGreen"]sudo -K[/COLOR]

It will kill sudo's timestamp.

Another method which is quite BAD is to delete timestamp files from  /var/run/sudo/$USER directory.
$ [COLOR="SeaGreen"]sudo ls -l   /var/run/sudo/$USER [/COLOR]

It contains files (timestamps) for all sudoed Terminal windows (0, 1, 3,...etc) and file "unknown" for all sudoed programs started from the desktop (menu).

---

### Post by pcomelade on 2007-01-09
$sudo -K 

sudo still don't ask for a password.

$ sudo ls -l /var/run/sudo/$USER 
ls: /var/run/sudo/pignatelli: No such file or directory

In fact there is not "/var/run/sudo/" directory. Should it be?

M;

---

### Post by pcomelade on 2007-01-09
I fixed the problem:

One I installed KDE-desktop for Ubuntu, I had problems with kdesu (never recognized my password). I looked in internet and found a solution to that in
[http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/](http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/)

In this page the author propose to add the following lines:

[super-user-command]
super-user-command=su

to "/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdeglobals"

when this is done, ubuntu no longer asks for a password when a "sudo" command is entered.
Is this possible? Any explanation to this?

I removed the code and now it seems to perform as expected.

Thanx all

M;

---

### Post by tarball on 2007-01-24
This occurs if you are a member of the 'sudo' group.

Open '/etc/group' and check which users are in 'sudo' group.

---

