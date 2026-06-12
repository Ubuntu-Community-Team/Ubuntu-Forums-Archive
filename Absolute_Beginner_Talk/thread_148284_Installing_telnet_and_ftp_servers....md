---
title: "Installing telnet and ftp servers..."
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by bluewomble on 2006-03-21
I'm trying to install telnet and ftp servers on my ubuntu machine, but can't work out how to...

First off, I need to say that I _know_ that telnet and ftp are insecure. But I find them convienient and it is just for a home network which is firewalled behind my router.

I have run:
sudo apt-get install telnetd
and
sudo apt-get install ftpd

but that doesn't seem to have installed them as a service... I still can't telnet or ftp to them...  How do I get it to work?  Do I need to put something in /etc/init.d/ or would that have been done by apt-get?

(By the way, I'm using Breezy Badger)

Thanks in advance,
Ash.

---

### Post by taurus on 2006-03-21
For telnet, use sshd; and for ftp, install vsftpd!!!

---

### Post by fatsamurai on 2006-03-21
There really is no advantage to using telnet over ssh. Just lot's of disadvantages. 

If you install the ssh server and you can use scp and sftp instead of ftp too.

---

