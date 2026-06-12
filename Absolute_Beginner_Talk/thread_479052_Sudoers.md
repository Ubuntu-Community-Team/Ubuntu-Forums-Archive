---
title: "Sudoers"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-06-19
Hey guys...I just need a quick favor

Could someone cat /etc/sudoers and post the results so I can do a comparison to mine.

Thank you very much!:p

---

### Post by rygar on 2007-06-19
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

---

### Post by isaacj87 on 2007-06-19
Thank you very much!

---

