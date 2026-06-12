---
title: "$Home dir error"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Demetrios on 2006-12-29
I loaded 6.06 on an old machine. I have created a sharefile but I keep getting this error when I logon.

User's $Home /.dmrc file is being ignored this represents the default session and language from being saved. File should be owned by user and have 644 permissions user's $Home directory must be owned by user and not writable by others uses. 

What does this mean. all I want to do is create asharefile were the kids can upload and download file like music, and games. 

I have attached a print of the samba conf file please help..

---

### Post by steve.horsley on 2006-12-29
Try setting the ownership to 644 then. Open a terminal and use this command to make sure you own the file (substitute your user name):
**sudo chown username:username ~/.dmrc**
and then set the permissions it wants:
**chmod 644 ~/.dmrc**

---

### Post by Demetrios on 2006-12-29
Thanks for the advise,

I get the following error

I enter     
sudo chown demetrios:demetrios~/.dmrc

reply is 
chown: missing operand after demetrios:demetrios~/.dmrc

---

### Post by freebeer on 2006-12-29
You need a space after "demetrios" and the "~", I think.  

ie:  sudo chown demetrios:demetrios**[space]**~/.dmrc

---

### Post by Demetrios on 2006-12-29
Thanks

I have tried your suggestion. I logged out and came back still the same error.

---

### Post by steve.horsley on 2006-12-29
Did you also **chmod 755 ~/.dmrc**?

If so, all I can think of is deleting the file and let whatever wants to recreate it:
**rm ~/.dmrc**
although renaming it might be safer because you can rename it back it it doesn't work out:
**mv ~/.dmrc ~/.dmrc-old**

---

