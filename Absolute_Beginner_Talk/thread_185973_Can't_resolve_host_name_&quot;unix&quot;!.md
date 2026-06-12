---
title: "Can't resolve host name &quot;unix&quot;!"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Getwild2 on 2006-06-01
I get this error message after executing pretty much any command in my terminal.  I get this message regardless of what command I enter.  For instance:

cstiff@ubuntu:~$ sudo gedit /etc/vsftpd.conf
Password:
Can't resolve host name "unix"!
cstiff@ubuntu:~$

Now the command does execute just fine, I just get this annoying line, "Can't resolve host name "unix"!".  

What does it mean and how might I rid myself of it?  It just started doing this recently.  I've been attempting to get an FTP server going, so maybe along the way I did something to cause this problem.  

Thanks for your help!!

---

### Post by Getwild2 on 2006-06-02
Just to provide more information, below I've pasted what my terminal looks like when I issue a few commands.  

cstiff@ubuntu:/etc$ sudo gedit vsftpd.conf
Password:
Can't resolve host name "unix"!
cstiff@ubuntu:/etc$ sudo gedit vsftpd.conf 
Can't resolve host name "unix"!
cstiff@ubuntu:/etc$ sudo gedit /inetd/inetd.conf 
Can't resolve host name "unix"!
cstiff@ubuntu:/etc$ cd /
cstiff@ubuntu:/$ sudo gedit /etc/indetd/inetd.conf 
Can't resolve host name "unix"!
cstiff@ubuntu:/$ sudo /usr/sbin/tcpd
Can't resolve host name "unix"!
cstiff@ubuntu:/$ sudo gedit /inetd/inetd.conf
Password:
Can't resolve host name "unix"!
cstiff@ubuntu:/$ sudo gedit /etc/resolv.conf 
Can't resolve host name "unix"!
cstiff@ubuntu:/$ sudo gedit /etc/rc.conf 
Can't resolve host name "unix"!
cstiff@ubuntu:/$

Any ideas?  Everything else works fine, internet, programs, etc.

---

