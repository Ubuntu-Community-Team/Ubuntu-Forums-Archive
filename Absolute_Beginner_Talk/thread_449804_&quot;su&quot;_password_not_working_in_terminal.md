---
title: "&quot;su&quot; password not working in terminal"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-05-20
I downloaded Xampp today which went well, but the terminal doesn't accept my password after typing in "su".

```
After downloading simply type in the following commands:

   1. Go to a Linux shell and login as the system administrator root:

      su
```
I keep typing su, then my password but it's not being accepted.  The terminal works fine otherwise and accepts my password for other things, example after I type "sudo" but not after "su".  How do I get this to work?

Thanks

---

### Post by taurus on 2007-05-20
```
sudo su
```

---

### Post by rich.bradshaw on 2007-05-20
or 

```
sudo -i
```

---

### Post by GoneWithTheWind on 2007-05-20
Thank you!

Now the next command for installation of Xampp::

```

Extract the downloaded archive file to /opt:

tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
```
gives me this:

```
@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/john# tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
tar: xampp-linux-1.6.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
@ubuntu:/home/#
```

What am I missing?

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by bashologist on 2007-05-20
"xampp-linux-1.6.1.tar.gz" isn't in your cd.

---

### Post by taurus on 2007-05-20
You need to be in the directory before you can unpack it to /opt.  Do you see **xampp-linux-1.6.1.tar.gz** from the output of this command?

```
ls -la
```

Try something like

```
cd /home/john/Desktop
ls -la
tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
```

---

### Post by GoneWithTheWind on 2007-05-20
> **taurus said:**
> You need to be in the directory before you can unpack it to /opt.  Do you see **xampp-linux-1.6.1.tar.gz** from the output of this command?
```
ls -la
```
Yes.

> Try something like

```
cd /home/john/Desktop
ls -la
tar xvfz xampp-linux-1.6.1.tar.gz -C /opt
```
That worked well and a long string came out.  However none of them opened, as below.

```
lampp/share/terminfo/x/xnuppc+112x37
tar: lampp/share/terminfo/x/xnuppc+112x37: Cannot open: No such file or directory
lampp/share/terminfo/x/xnuppc+128x40
tar: lampp/share/terminfo/x/xnuppc+128x40: Cannot open: No such file or directory
lampp/share/terminfo/x/xnuppc+128x48
tar: lampp/share/terminfo/x/xnuppc+128x48: Cannot open: No such file or directory
lampp/share/terminfo/x/xnuppc+144x48
tar: lampp/share/terminfo/x/xnuppc+144x48: Cannot open: No such file or directory

```

This is what I get with ls -la .
```
john@ubuntu:~/Desktop$ ls -la
total 62256
drwxr-xr-x  5 john john     4096 2007-05-20 06:36 .
drwxr-xr-x 34 john john     4096 2007-05-20 18:52 ..
drwxr-xr-x  9 john john     4096 2006-09-27 22:07 camorama-0.17
-rw-r--r--  1 john john  1171800 2007-05-15 09:00 dlsetup.exe
drwxr-xr-x 13 john john     4096 2007-05-14 14:46 firefox
-rw-r--r--  1 john john  9651693 2007-05-14 09:33 firefox-2.0.0.3.tar.gz
-rw-r--r--  1 john john    13687 2007-05-14 13:06 installnewfirefox_3.1.1.sh
drwxr-xr-x 20 john john     4096 2007-04-17 09:13 lampp
-rw-r--r--  1 john john 52804323 2007-05-20 06:28 xampp-linux-1.6.1.tar.gz
john@ubuntu:~/Desktop$

```

---

### Post by taurus on 2007-05-20
Can you post the output of this command here?

```
tar tvzf xampp-linux-1.6.1.tar.gz
```

---

### Post by GoneWithTheWind on 2007-05-20
That worked - thank you!

```
-rw-r--r-- root/root      1604 2003-01-05 07:13:12 lampp/share/terminfo/w/wy-75ap
-rw-r--r-- root/root      1271 2003-01-05 07:13:11 lampp/share/terminfo/w/wy-99fgt
-rw-r--r-- root/root      1261 2003-01-05 07:13:11 lampp/share/terminfo/w/wy120-25-w
-rw-r--r-- root/root       471 2003-01-05 07:13:11 lampp/share/terminfo/w/wy100
-rw-r--r-- root/root       428 2003-01-05 07:13:12 lampp/share/terminfo/w/wy100q
-rw-r--r-- root/root      1257 2003-01-05 07:13:11 lampp/share/terminfo/w/wy120
-rw-r--r-- root/root      1263 2003-01-05 07:13:11 lampp/share/terminfo/w/wy120-25
.
. etc
.
drwxr-xr-x root/root         0 2007-04-12 23:55:56 lampp/var/proftpd/
-rw-rw-r-- root/root      2232 2007-03-23 11:55:04 lampp/var/proftpd/proftpd.delay
drwxr-xr-x root/root         0 2005-05-31 04:00:59 lampp/var/run/
-rw-rw-r-- root/root         5 2005-05-31 04:13:38 lampp/var/run/ddclient.pid
-rw-rw-r-- root/root     45571 2007-04-17 09:13:18 lampp/RELEASENOTES
-rwxr-xr-x root/root     14460 2007-03-05 06:26:02 lampp/lampp
drwxr-xr-x root/root         0 2006-04-26 10:46:11 lampp/libexec/
john@ubuntu:~/Desktop$
```

Thanks very much. Does that mean it's all installed where it should be?   Will try the next step now.  ;)

---

### Post by GoneWithTheWind on 2007-05-20
Disappeared again.

```
john@ubuntu:~/Desktop$ /opt/lampp/lampp start
bash: /opt/lampp/lampp: No such file or directory
john@ubuntu:~/Desktop$
```

---

### Post by taurus on 2007-05-20
Actually, it didn't unpack anything.  Just wanted to make sure the file is alright.

Here is what you should do, as a regular user--john.

```
cd ~/Desktop
sudo cp xampp-linux-1.6.1.tar.gz /opt
cd /opt
sudo tar xvzf xampp-linux-1.6.1.tar.gz
```
Now, it is unpacked in /opt.

---

### Post by GoneWithTheWind on 2007-05-20
Wonderful.  Thank you for your time and guidance, Taurus.

```

.
.
.
lampp/var/mysql/test/testad.frm
lampp/var/mysql/test/testac.MYD
lampp/var/mysql/test/testac.frm
lampp/var/mysql/test/testai.frm
lampp/var/mysql/mysql_upgrade_info
lampp/var/proftpd/
lampp/var/proftpd/proftpd.delay
lampp/var/run/
lampp/var/run/ddclient.pid
lampp/RELEASENOTES
lampp/lampp
lampp/libexec/
john@ubuntu:/opt$
john@ubuntu:/opt$ /opt/lampp/lampp start
You need to start XAMPP as root!
john@ubuntu:/opt$
```

Update:  It's loaded.  
```
john@ubuntu:/opt$ cd /
john@ubuntu:/$ /opt/lampp/lampp start
You need to start XAMPP as root!
john@ubuntu:/$ sudo /opt/lampp/lampp start
Password:
Starting XAMPP for Linux 1.6.1...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
john@ubuntu:/$
```

---

### Post by GoneWithTheWind on 2007-06-11
I'm trying to start Xampp from the terminal. This is what happens:

> john@ubuntu:~$ /opt/lampp/lampp start
You need to start XAMPP as root!

> john@ubuntu:~$ cd /opt
john@ubuntu:/opt$ john@ubuntu:~$ /opt/lampp/lampp start
bash: john@ubuntu:~$: command not found
john@ubuntu:/opt$ You need to start XAMPP as root!
bash: You: command not found
What do I need to do to start Xampp, and how can I move it to the panel?

Thanks  :)

---

### Post by taurus on 2007-06-11
As the message said, you need to start it as root.

```
**sudo** /opt/lampp/lampp start
```

---

### Post by GoneWithTheWind on 2007-06-11
Thanks, that worked.  :)

Is there a way to put a xampp icon in the panel and start it from there?

---

