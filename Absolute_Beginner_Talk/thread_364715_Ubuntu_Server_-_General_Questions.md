---
title: "Ubuntu Server - General Questions"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by uberamd on 2007-02-18
I was able to get Apache and PHP installed and working. I also got MySQL installed and working. My first question is how do I enable MySQL to allow outside connections (from remote applications, etc). I read that it involved changing the bind IP, so I changed it to my server address warezhost.org (not actually a warez site), but then MySQL would not start complaining that it could not find MySQL.sock. If I changed it back to localhost, it started with no problems.

Second: I got vsftpd installed, but I can not figure out how to create a user that can FTP to my apache directory (ex /var/www), I always get 500 Permission Denied even though I did a chmod 777 /var/www

Lastly: I need to download files from a SVN location, and I have no x-windows installed, is it possible to do it without x-windows?

Thanks in advance.

---

### Post by spoot on 2007-02-19
Wouldn't know the answer to your first two questions. But this one:
> **uberamd said:**
> Lastly: I need to download files from a SVN location, and I have no x-windows installed, is it possible to do it without x-windows?
Thanks in advance.
Certainly, in fact that is the most common way I think ;)

The "subversion" package installs the text-based svn client, try a "svn help" to see how it works.

---

### Post by uberamd on 2007-02-19
Thank you for answering that :)

---

### Post by spoot on 2007-02-21
> **uberamd said:**
> Thank you for answering that :)
Not a problem :)

Regarding your second problem, perhaps you set the chroot options on (or they are on by default) in /etc/vsftpd.conf. If this is the case the top directory ftp users will see is their home folder probably, so going outside it might give a permission error. Not really sure on all of this but it's worth a shot :KS

---

