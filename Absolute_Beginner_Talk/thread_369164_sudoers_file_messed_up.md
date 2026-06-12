---
title: "sudoers file messed up"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-02-24
I have a problem since adding firestarter to the sudoers file.  Now every time I enter sudo or gksudo my system just opens the file or program requested without asking for a password.  Say if I enter gksudo nautilus, nautilus just opens.  I am posting my sudoers file here:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: ALL

terminator ALL= NOPASSWD: /usr/bin/firestarter

Please let me know what I have to change to get ubuntu back to asking for a password after the sudo or gksudo command.

---

### Post by alienexplorers on 2007-02-24
Bump

---

### Post by alienexplorers on 2007-02-24
Noticed under admin NOPASSWD: should not be there.  Removed and now everything works OK.

---

### Post by george29 on 2007-02-24
why did you add firestarter to sudoers? 

try changing the section 
#Members of the admin group may gain root priviliges
%admin ALL=(ALL) : ALL

remove the firestarter section

so it looks like below:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL): ALL

---

### Post by alienexplorers on 2007-02-24
This way it starts firestarter up with out entering a password.  It's syntax is:
username ALL= NOPASSWD: /usr/bin/firestarter

Then under sessions you would enter:
sudo firestarter --start-hidden 

Now firestarter starts at each boot in the background.

---

### Post by TheWizzard on 2007-02-24
> **alienexplorers said:**
> This way it starts firestarter up with out entering a password.  It's syntax is:
username ALL= NOPASSWD: /usr/bin/firestarter

Then under sessions you would enter:
sudo firestarter --start-hidden 

Now firestarter starts at each boot in the background.


why?
firestarter is not your firewall. firestarter is only a gui to edit iptables (your firewall). 
starting firestarter all the time is a possible security tread.

regarding your problem:
did you make a backup? some editors do automatically. use the backup to restore your file. 
make sure you always make backups if you edit files. also make a weekly backup of your /etc directory.

---

### Post by aysiu on 2007-02-24
This should help you get back the default /etc/sudoers file:
[http://psychocats.net/ubuntu/sudo](http://psychocats.net/ubuntu/sudo)

---

