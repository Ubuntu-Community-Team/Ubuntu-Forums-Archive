---
title: "Limited SSH account"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jmknash on 2007-12-03
Hi
I have a user account called 'tunnel', and this is for an outside insecure connection for a client just for making a reverse tunnel to itself and also use my proxy for the internet.

It has the UID code 65534 and when it logs in it to my server it has nobody@192.16.... but the user can still browse all the file and open with vi or nano and read files I want to block it from having any access to free roam around the system, so a very limited account. can anyone help? 
Jon

---

### Post by HermanAB on 2007-12-03
Google for "ssh chroot".

Cheers,

Herman

---

### Post by jmknash on 2007-12-03
Thanks, seems complicated to set up tho, I'll try it out.

---

### Post by Peter LaValle on 2007-12-03
90% of Linux is hopelessly complicated to everyone, but that is the 90% they need.

---

### Post by jmknash on 2007-12-03
lol true.
I found one tutorial which worked for me [http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/](http://www.fuschlberger.net/programs/ssh-scp-sftp-chroot-jail/)

---

### Post by HermanAB on 2007-12-03
If that is too complex, then configure a special group, make the remote users members of that group and configure /etc/sudoers such that they can only do a very limited number of things.  Sudo gives you very fine grained control and is likely more secure than chroot ssh.  Read the sudoers man page for details - very easy to do.

Cheers,

Herman

---

