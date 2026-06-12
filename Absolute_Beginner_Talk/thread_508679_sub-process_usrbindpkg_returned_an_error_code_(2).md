---
title: "sub-process /usr/bin/dpkg returned an error code (2)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Leonin on 2007-07-24
I get this message when I try to aptitude install a  ftp server: sub-process /usr/bin/dpkg returned an error code (2).
Any ideas on what's wrong?

---

### Post by Foxmike on 2007-07-24
Can you copy/paste here the whole terminal output?

---

### Post by Leonin on 2007-07-24
Here it is > mikael@wahlin:~$ sudo aptitude install vsftpd
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  vsftpd
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/114kB of archives. After unpacking 418kB will be used.
Writing extended state information... Done
dpkg: syntax error: unknown user `postfix' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
mikael@wahlin:~$     

---

### Post by nitro_n2o on 2007-07-24
I'm not sure how to fix this, but certainly there was something wrong with postfix installation that you attempted before 
try: 
sudo dpkg-reconfigure postfix 
or 
sudo dpkg-reconfigure -a 
I'm not sure which one though, i'm not front of my ubuntu
hope that helps

---

### Post by Leonin on 2007-07-24
That looks like right, but I have no idea what option I should choose while reconfiguring.
Thank you for your help. :)

---

### Post by tomcheng76 on 2007-07-24
sudo gedit /var/lib/dpkg/statoverride

delete the postfix line

---

### Post by Leonin on 2007-07-24
That made it much better, but now I'm getting this error log: > mikael@wahlin:~$ sudo aptitude install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up vsftpd (2.0.5-2ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up vsftpd (2.0.5-2ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing vsftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vsftpd


---

### Post by Foxmike on 2007-07-24
Do you still have that file open?  Or do you have anoyher instance of apt/synaptics/add/remove running in background?

---

### Post by Leonin on 2007-07-24
No its closed. The only thing that I have open is Gaim, Firefox, Azureus and Amarok.

---

### Post by Leonin on 2007-07-24
Anyone?

---

### Post by Leonin on 2007-07-25
I really need to get this working so I have to try a bump more. :)

---

