---
title: "Can't access admin programs."
date: 2006-01-22
forum: Absolute Beginner Talk
---

### Post by LinuX Nova on 2006-01-22
Hey.

I tried to use symantec today, and discovered that when i click to open it, nothing happens, it shows no signs of loading, a little research later shows that I cannot open any of the programs under Systme => Administrator.

How can this be, seing as I am the admin of this coomputer.

Does anyone know whats wrong/or can offer some advice as to what the problem may be?

P.s, I am running breezy badger.

My sudoers file says the following:
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

### Post by bscbrit on 2006-01-22
Your sudoers file confirms that both root and admin group members have sudo access, so perhaps you are not a member of the admin group?

Try the following on the command line:

groups <username>

Make sure that 'admin' is in the list of groups to which you belong.  If it isn't there, then the following should cure that problem:

sudo adduser <username> admin

---

### Post by bscbrit on 2006-01-22
Of course, if you don't have access to the sudo command, you probably will not be able to add yourself to that group using 'sudo' - sometimes I'm not very bright!

Reboot into recovery mode, which will bring you to the command line as root, and enter the commands from there.  If you cannot even get to the command line in recovery mode then your problem is not a simple one and you had better come back here to let us know about it!

---

### Post by LinuX Nova on 2006-01-22
I can use the cmd prompt, and when i type "groups paul(that's my username)"  i get 

"paul adm dialout cdrom floppy audio dip video plugdev ipadmin scanner admin"

---

### Post by bscbrit on 2006-01-24
OK, well there appears to be nothing wrong with the sudoers file or your group membership.  Try the following on the command line:

sudo synaptic

This should start synaptic without going through the menu - I'm just checking whether your menu links are corrupted, or whether your program has an installation problem.

Sorry for the slow response - I've had problems getting back onto the forums, as have many others I believe....  :D

---

