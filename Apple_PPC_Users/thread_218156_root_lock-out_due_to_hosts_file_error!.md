---
title: "root lock-out due to hosts file error!"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by mikkel_j on 2006-07-18
Hi there,

I have a remote server running Ubuntu 6.06

While setting up Tomcat I manually edited the /etc/hosts file and removed the entry containing the server name alias (major boo-boo)

Now when I reboot I cannot use "sudo bash" instead I get following error

sudo: unable to lookup your-server-name via gethostbyname()

My problem is that I can't change the hosts file back without becoming root, so what do I do???

Regards

- Mikkel

---

### Post by udha on 2006-07-18
try some of these:

sudo -s
su -
su

you could also try changing the init level, if the machine isn't live.

Last resort would be to fire up a live distro and edit the file that way.

---

