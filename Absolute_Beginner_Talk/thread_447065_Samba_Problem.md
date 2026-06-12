---
title: "Samba Problem"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-05-17
OK, I installed SAMBA on my network drive server, how do I make a network path for it? So that I can connect to it with my Windows PC, and how do I add a PC to the Samba network?

---

### Post by Quintin Riis on 2007-05-17
Read the manual pages, thanks.  

[http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

User home directories work automagically, but because NT and Unix hash passwords differently, you need to run "smbpasswd -a" for each user and put in the right password.  Then you can get at that user's home directory at \\myserver\\myuser.

---

