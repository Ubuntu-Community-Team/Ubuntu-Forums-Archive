---
title: "SUDO doesn't work?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Pawka on 2005-12-15
As i know, after installed Ubuntu, access to sudo gets the first created user. I instaled Ubuntu and started it. I've got message that there are 37 updates availabale. I've tryed to view them, entered password, but nothing happends. Also i can't run such tools as "Synaptic package manager", "Users and groups" and others. Finaly i've entered at console this:
```
sudo -l
```
and i have got this one:
```
Sorry, user as may not run sudo on 10.
```
I've tryed load Ubuntu as root user, added a new user, but, because i'm new at linux, results were the same. What you suggest to do?

---

### Post by Mustard on 2005-12-15
sudo privileges are determined by the entry in the /etc/sudoers file.  You can edit this file with a specific command that is designed to edit just this one file.  I'm assuming you can do this as root, as you seem to have done something as root in your post above.

The command is ...
```
visudo
```

An example of what a /etc/sudoers file looks like is this...

```
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
mustard ALL=(ALL) ALL

```

Note the user 'mustard' has been given the same privileges as the 'root' user.  If you copy the last line into your own sudoers file, subsituting your username for 'mustard' then save the file, you should have sudo access.

Some sudoers files don't use the actual user name, but instead have an entry called %admin.  This denotes an admin group.  If you use %admin instead of the actual username, then that user will be required to be added to the 'admin' group before they are able to have sudo privileges.

---

### Post by Pawka on 2005-12-15
Thank you. I've got what i need. Everything works now :-)

---

