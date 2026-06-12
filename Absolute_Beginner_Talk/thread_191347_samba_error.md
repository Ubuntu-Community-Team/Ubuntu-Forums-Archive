---
title: "samba error"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-07
trying to gety a folder to share with samba this is the error i'm getting

An error occurred while trying to share folder '/home/john/Desktop/mp3'. Make sure that the Perl script 'fileshareset' is set suid root.

Any ideas on how to fix or what i missed?

---

### Post by Jagot on 2006-06-07
You could have a look at the guide here to see if you're doing it correctly:

[http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

---

### Post by armware on 2007-06-18
i had this myself.
if you've set file sharing to 'advanced sharing' and try to enable a share using the 'simple sharing' method (in the folder properties dialog, for example) it'll give you that message.
change file sharing to 'simple' and try it again.
what i say isn't gospel - it just worked for me, and that's how i see it.

---

