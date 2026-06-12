---
title: "lost admin"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-18
I've been gone a couple of days and just returned.  Before I left, I was playing with groupadd groupmod usermod.  I read several places explaining these commands including the man pages, but I didn't (and still don't) fully understand.  I succeeded in creating a family group.  And I succeeded in making myself a member of this group. 

Now, I realize that somehow I errased my membership in all other groups including the admin.  I can't sudo anything or use the System>administration GUI.  I tried to gedit the group file, but it is read only for my user name.  

Is there any way to work around this besides reinstalling?

---

### Post by Mustard on 2006-02-18
The grub menu has a 'recovery mode' option which will drop you to a root prompt.  From there you would use the visudo command to add yourself back to the /etc/sudoers file, or add yourself back to the admin group if you use %admin in sudoers file.

---

### Post by bountonw on 2006-02-18
ok.  Succeded in booting in recovery and read the greek man pages of visudo.  I typed in the visudo command and opened up sudoers, like you say.  

Most of the lines were commented out.  Where do I put my user name?

---

### Post by Mustard on 2006-02-18
[QUOTE=bountonw]ok.  Succeded in booting in recovery and read the greek man pages of visudo.  I typed in the visudo command and opened up sudoers, like you say.  

Most of the lines were commented out.  Where do I put my user name?[/QUOTE]

You would add a line at the bottom using your username, as demonstrated by my sudoers file below....

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

---

### Post by bountonw on 2006-02-18
It worked.  Thank you.

---

