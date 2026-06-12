---
title: "Make sudo ask for password every time"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by gsub on 2007-12-17
Hi, all

i'm trying to get sudo to ask me for a password every time i use it. i know that i need to change the timestamp value to 0 instead of the default 15. what i don't know is the syntax and place to enter it in my sudoers file. Could someone please help? Below is a copy of my sudoers file.

Many thanks!



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

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by jken146 on 2007-12-17
[http://ubuntuforums.org/showthread.php?p=116697#post116697](http://ubuntuforums.org/showthread.php?p=116697#post116697)

---

