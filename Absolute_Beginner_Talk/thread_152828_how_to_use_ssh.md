---
title: "how to use ssh?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by foxy123 on 2006-03-30
being with Ubuntu for a while I have never use ssh. I wonder if it is possible to copy a file from one PC to another in the network using ssh and could it be faster than samba?

---

### Post by Jason_25 on 2006-03-30
I don't know if it's any faster than samba but you can use sftp.
```

sftp username@host

```
Then you would use the get and put commands to download and upload.

---

### Post by kmi on 2006-03-30
Yes it is possible just as a normal remote copy once your connected through ssh.
scp (secure copy protocol, I guess) is made to do the trick (I use Fugu in MacOSX, Putty in w!nd0w5 shall be good at it too...)
ssh/scp vs. samba ? security is obvious... for the speed... you certainly will report once you have carefully tested it ;)

edit : [scp]("http://en.wikipedia.org/wiki/Secure_copy")

---

### Post by OffHand on 2006-03-30
if you want speed use ftp. ssh is way slower.

---

### Post by johnnymac on 2006-03-30
Don't use FTP it's a security hole....username and passwords are passed from host to remote via plain text

you want to move a file from one linux to another....

copy from host to remote:
scp <filename> user@remote:/<location>

copy from remote to host
scp user@remove:/<location on remote> <location on host>

copy entire directory
scp -r <directory> user@remote:/<location>

---

### Post by foxy123 on 2006-04-26
I cannot understand something. If I do 
```
:~$ ssh foxy@ubuntu
```
I've got
```
ssh: thehill: Name or service not known
```

However if I do 
```
:~$ ssh foxy@195.145.1.4
```
I successfully connect to a remote computer:
```
~$ ssh foxy@195.145.1.4
foxy@195.145.1.4's password:
Linux ubuntu 2.6.15-21-686 #1 SMP PREEMPT Fri Apr 21 16:57:03 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Apr 26 18:14:51 2006 from 192.168.1.3
foxy@ubuntu:~$

```
Why I cannot use a host name?

---

### Post by macdo on 2006-04-26
Add this line into /etc/dhcp3/dhclient.conf ```
send host-name "ubuntu";
```
Remeber to back up the file first, though!

Alternatively, edit (or create) a file in /etc containing the line ```
ubuntu
```

As you may have guessed, I'm not entirely sure about either of these, so tell us how it went :-)

---

### Post by AndyCooll on 2006-04-26
THis is because your pc doesn't know what address your "ubuntu" box has. To use a remote pc's hostname you first need to have it listed in /etc/hosts on the client (i.e. the pc you are connecting _from_). So:

```
sudo gedit /etc/hosts
```

Then add a line that looks something like this:

```
ubuntu 195.145.1.4
```

You can then type:

```
ssh ubuntu
```

:cool:

---

### Post by foxy123 on 2006-04-26
so if I do not have a static IP I cannot use it?

---

### Post by auroraborealis on 2006-04-26
Use a dynamic dns service (it's free).

[http://www.dyndns.com](http://www.dyndns.com)

---

### Post by az on 2006-04-26
[QUOTE=auroraborealis]Use a dynamic dns service (it's free).

[http://www.dyndns.com](http://www.dyndns.com)[/QUOTE]
Install ddclient if you are directly hooked up to your modem, or see if your router can be a client to a dynamic dns server.  In the latter case, you will have to forward the port (22) to your ubuntu box on your lan.

---

