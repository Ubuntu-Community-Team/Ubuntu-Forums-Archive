---
title: "sudo never ask me the password"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by kufio on 2007-03-16
I am the only admin user on this box and when I type for example "sudo nautilus" it does not ask me the password. I have checked my  /etc/sudoers file and it look like this


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,timestamp_timeout=0

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by 23meg on 2007-03-16
You should use *gksudo* instead of *sudo* with graphical apps such as Nautilus. What output do you get in the terminal when you type "gksudo nautilus"?

---

### Post by bapoumba on 2007-03-16
What does return **groups**?
sudo will not prompt you for password for 5 mins (I think) by default, after a first password prompt.

---

### Post by kufio on 2007-03-16
this is what I get with gksudo nautilus, but it opens the graphic desktop as root

(nautilus:6376): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

---

### Post by kufio on 2007-03-16
> **bapoumba said:**
> What does return **groups**?
sudo will not prompt you for password for 5 mins (I think) by default, after a first password prompt.

it never ask me the password

---

### Post by 23meg on 2007-03-16
It probably has to do with the default timeout. Is it that it asks you for the password once, and then doesn't for some time? The timeout is 15 minutes; once you type the password for one operation, it won't ask for it for the next 15 minutes.

---

### Post by kufio on 2007-03-16
> **23meg said:**
> It probably has to do with the default timeout. Is it that it asks you for the password once, and then doesn't for some time? The timeout is 15 minutes; once you type the password for one operation, it won't ask for it for the next 15 minutes.

no it never ask me for the passwd, not even the 1st time I open the terminal

---

### Post by Lord Illidan on 2007-03-16
What groups are you a member of?

Type ```
groups
``` in the terminal to check.

---

### Post by Lord Illidan on 2007-03-16
> **23meg said:**
> It probably has to do with the default timeout. Is it that it asks you for the password once, and then doesn't for some time? The timeout is 15 minutes; once you type the password for one operation, it won't ask for it for the next 15 minutes.

**timestamp_timeout**
 Number of minutes that can elapse before **sudo** will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.According to his layout, it should always ask him for a password.

EDIT : got this from [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by 23meg on 2007-03-16
Does the application whose name you type after "sudo" run? If it does, does it run as root?

Reboot, type "sudo -i" without running any administrative apps, and see if it asks for the password.

---

### Post by kufio on 2007-03-16
> **Lord Illidan said:**
> What groups are you a member of?

Type ```
groups
``` in the terminal to check.

the groups I am in:


sudo adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

---

### Post by 23meg on 2007-03-16
> **Lord Illidan said:**
> According to his layout, it should always ask him for a password.


I missed that part in the OP's file; in my default Edgy sudoers file, I have no timestamp_timeout value, and as far as I know, the default is 15 minutes.

---

### Post by kufio on 2007-03-16
> **23meg said:**
> Does the application whose name you type after "sudo" run? If it does, does it run as root?

Reboot, type "sudo -i" without running any administrative apps, and see if it asks for the password.

I rebooted, typed sudo -i, and it did not ask for the passwd, weird thing!!
yes the application run when I type "sudo"

---

### Post by scxtt on 2007-03-16
> **kufio said:**
> the groups I am in:


sudo adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admintry removing yourself from the "sudo" group ...
(note: you probably have to logout/login for the change to take effect)

---

### Post by Lord Illidan on 2007-03-16
> **kufio said:**
> the groups I am in:


sudo adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner admin

Try making a new account from System -> Administration -> Users and Groups.
See if that works.

And I think you have to delete yourself from the sudo group.

---

### Post by kufio on 2007-03-16
Ok, I removed myself and now it ask for the passwd, I am now in group "users"

---

