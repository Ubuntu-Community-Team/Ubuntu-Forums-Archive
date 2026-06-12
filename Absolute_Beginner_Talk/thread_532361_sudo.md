---
title: "sudo"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by ElSean on 2007-08-22
Does any have the command I've gotten put into my sudoers file to make the sudo login remember to 0?

---

### Post by wirelessmonkey on 2007-08-22
What are you really asking?
My first impression is that you're asking what you need to add to your sudoers file so that you login automatically? Automatically as root?

---

### Post by schorsch on 2007-08-22
This is an option in the file /etc/sudoers
```
man sudoers
```
--> timestamp_timeout
                   Number of minutes that can elapse before sudo will ask for a passwd again.  The default is 15.  Set this to 0 to always prompt for a
                   password.  If set to a value less than 0 the user&#8217;s timestamp will never expire.  This can be used to allow users to create or delete
                   their own timestamps via sudo -v and sudo -k respectively.


I do not know if you want to be always asked for the password or never after giving it once ...

---

