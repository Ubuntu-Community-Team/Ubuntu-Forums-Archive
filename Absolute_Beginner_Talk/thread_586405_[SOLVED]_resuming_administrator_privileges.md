---
title: "[SOLVED] resuming administrator privileges"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-10-22
Hi

I don't know if this is a weird question but can one make the system ask for a password everytime an administrator privilege is required.
For example, if I enter the password when opening 'synaptic' once, then it does not ask for the password until few minutes have passed. 
 Is it possible to change the time duration or reset to user privileges whenever I wish?

---

### Post by realvz on 2007-10-22
Yes you can do it...
you can change the time limit in the visudo file
[http://www.gratisoft.us/sudo/man/visudo.html](http://www.gratisoft.us/sudo/man/visudo.html)
here is the link that has a manual about visudo

alternatively you can also do sudo -K manually to make ur system end sudo session

---

### Post by 5-HT on 2007-10-22
timestamp_timeout in /etc/sudoers will to the trick:

[quote=sudoers manual] timestamp_timeout
                       Number of minutes that can elapse before sudo will ask
                       for a passwd again.  The default is 5.  Set this to 0
                       to always prompt for a password.  If set to a value
                       less than 0 the user's timestamp will never expire.
                       This can be used to allow users to create or delete
                       their own timestamps via sudo -v and sudo -k respec-
                       tively.
 [/quote]

---

### Post by genbuntu on 2007-10-22
Thanks for the replies. but I cannot open the sudoers file. It says  "Cannot open /etc/sudoers: No application suitable for automatic installation is available for handling this kind of file. ".
I've tried with text editor also.

---

### Post by 5-HT on 2007-10-22
> **genbuntu said:**
> Thanks for the replies. but I cannot open the sudoers file. It says  "Cannot open /etc/sudoers: No application suitable for automatic installation is available for handling this kind of file. ".
I've tried with text editor also.
Editing it by running 'sudo visudo' (in a terminal) is the preferred way as it'll automagically check for syntax errors. On ubuntu, that command should open up the file in nano.

cheers,

---

### Post by realvz on 2007-10-22
> **genbuntu said:**
> Thanks for the replies. but I cannot open the sudoers file. It says  "Cannot open /etc/sudoers: No application suitable for automatic installation is available for handling this kind of file. ".
I've tried with text editor also.

sudo visudo??
it should open the file in nano...
try it and let know

---

### Post by genbuntu on 2007-10-22
yes now it does open it but being a newbie I'll have to ask you guys how to fit in the timestamp option. Do I need to add another line of code? This is what the file contains: 

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

### Post by realvz on 2007-10-22
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn**,timestamp_timeout=0 **

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by genbuntu on 2007-10-22
One last step: How do I save it? I can't see any option to save it in the menu and it doesn't get saved if I close the window. (Sorry for being soo inexperienced)

---

### Post by realvz on 2007-10-22
ctrl +x ...and then press Y..to save

---

### Post by genbuntu on 2007-10-22
Thanks a lot. It works! :)

---

### Post by realvz on 2007-10-22
aha!

Enjoy Ubuntu

---

