---
title: "SSH server setup question"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-11-04
hey there, ive setup a ssh server on my ubuntu 7.10, i tested this and it works well, the thing is when i allow a user to connect to me, i dont want them to be able to access/view the system files, i only want the login users to be able to access/view/modify etc the files in there home directory, how do i go about this? ive heard something about rbash, although im not too sure how to set this up, help much appreciated!

---

### Post by HermanAB on 2007-11-04
There is a way to 'chroot' SSH.  Some googling will find it.  However, don't trust a chroot too much, since it is possible to break out of it.

---

### Post by dynamethod on 2007-11-05
ahh interesting! this is what im looking for, however is there a more up to date release specifically for ubuntu?

---

### Post by hyper_ch on 2007-11-05
[http://www.howtoforge.com/mysecureshell_sftp_debian_etch](http://www.howtoforge.com/mysecureshell_sftp_debian_etch)

[http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)

Both written for Debian but should be apply also for Gutsy.

---

### Post by Bachstelze on 2007-11-05
Ubuntu uses OpenSSH as it's SSH implementation, which does not support chrooting by default, so setting it up can be quite tricky.

However, do you really need SSH ? If all you want is give users access to their files, FTP might be a good idea.

---

### Post by dynamethod on 2007-11-05
hmm seems im having trouble with SSH now, i tested the server by using ssh localhost but i get:

ssh: connect to host localhost port 22: Connection refused

ive been using lokkit as a firewall, but in the lokkit setup i selected the option to allow SSH connections

help needed :S

---

