---
title: "Major security risk?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Jloser on 2008-01-31
I want to setup a new box to do the following:

serve a small basic webpage
allow remote (ssh) logins to update the website
be the "backup location" for the rest of my PC's so I can access all my files remotely

How big of a security risk is this?  Should I use separate PC's?  Why or why not?  What if I constantly monitor log files and watch for attacks?

---

### Post by ctyc on 2008-01-31
Just use Ubuntu and keep your box up to date with all the security patches related to any software you are running and it will be fine.

Looking at log files too much will only make you paranoid.

---

### Post by Rocket2DMn on 2008-01-31
You should only have the ports open on that machine for apache and ssh/sftp.  You can set those with firestarter which is a GUI to access iptables, the built in firewall in linux.  If you're behind a router, just forward those ports to the internal IP address of the server (like use static internal IP).
You may want to consider having your ftp server program running on a different port than the default one as an extra precaution.

---

### Post by oedha on 2008-01-31
keep update......
keep update the ssh password.....
advanced : make it only can be controlled by your machine only.....set the iptables....you can use firestarter....

~E~

---

### Post by Jloser on 2008-01-31
So as long as I keep the PC up to date, change the ports to random ports, and use *Good* passwords, everything should work out just fine?

Should I store personal information on a separate partition than everything else, any benefit to that?

---

### Post by Rocket2DMn on 2008-01-31
Here are two great resources on security:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
You should definitely read those, they are full of good information.

---

### Post by chewearn on 2008-01-31
AstalaVista says: don't put all eggs in one basket.

---

### Post by Jloser on 2008-01-31
So if I have one PC with port 80 open for http, then another one with an ftp server on port 2426 how is that any more secure than one PC to do both?  If someone can locate the ports, they can try and gain access right?

---

### Post by Rocket2DMn on 2008-01-31
It's not any more secure.  Just lock down the machine for everything but ftp and apache.

---

### Post by emarkd on 2008-01-31
They can only gain access if the software on that port is flawed.  Apache is very secure, so don't worry about it.  Changing the ftp port is false security at best, because a quick port scan would reveal the open port for probing.  I would recommend using ssh/scp for file transfer instead of ftp, just for the encryption.  If you're going to be mounting those "backup" directories in your other computers, you can do this with samba or sshfs and skip ftp altogether.

---

### Post by jflaker on 2008-01-31
> **Jloser said:**
> So if I have one PC with port 80 open for http, then another one with an ftp server on port 2426 how is that any more secure than one PC to do both?  If someone can locate the ports, they can try and gain access right?

It is more secure in that to lose a single machine to being compromised, you lose both the web and data.  

Linux is far more secure than Window$.  Even for dynamic websites, the database is never on the same system as the web services.

Always backup!

---

### Post by fain on 2008-01-31
I use denyhosts for my ssh server. Works great in preventing brute force hackers. Its in ubuntu's repo.

---

### Post by bodhi.zazen on 2008-01-31
ssh needs to be secured a little.

Change the default port, use keys, edit /etc/ssh/sshd_config to allow a limited list of users (and / or IP), install denyhosts

See this link : [uwiki]AdvancedOpenSSH[/uwiki]

If you do that you should be fine. Store backups off site (you can use scp).

---

