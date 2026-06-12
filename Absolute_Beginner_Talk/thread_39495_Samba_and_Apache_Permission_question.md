---
title: "Samba and Apache Permission question"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by dping28 on 2005-06-05
Hi, I have just installed Ubuntu and installed apache/mysql/php and samba. currently in order to add/edit/remove files/pages in /var/www for my site I have to be root. Could someone tell me the correct way to alter the permissions of this directory so I can do all this with say "user1". and currently I can access this machine from windows with said "user1" and view that users home directory. Could you also tell me the correct way to add /var/www for that user so I can edit these files from my windows boxes. Thanks!

-D

---

### Post by intangible on 2005-06-17
What I would do is this:
**sudo chown -R user1 /var/www**
and then, as user1 or with sudo:
**ln -s /var/www /home/user1/www** because you can already see that with samba.

I think a better solution instead of samba, is to install ssh on the machine and then connect to it from Windows using FileZilla [http://filezilla.sf.net](http://filezilla.sf.net) - That way you can manage permissions correctly, because Samba sharing does not allow you to manage permissions easily (just wait till you try to copy CGI files using SAMBA and making them work).

---

