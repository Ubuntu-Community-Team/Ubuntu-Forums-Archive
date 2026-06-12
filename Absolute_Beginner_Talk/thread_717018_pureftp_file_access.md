---
title: "pureftp: file access"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ojve on 2008-03-06
Hi!

This might be more of a general linux question than a Ubuntu-specific one.

I would like to know how to control file access on my linux platform running pureftp. Its embedded software so I dont think I can use a manager. I have looked at the pureftp documentation but so far I have only been able to set the home directory of a user and not control anything else.

The things I would like to be able to control are
- access to folders and their contents by individual groups
- access to folders and their contents by individual users, not just all other users than the owner.
- read/write and read-only access by individual groups and users

Is this possible? chmod doesn't do it and neither does chroot:(

Help plz!

//T

---

### Post by blastus on 2008-03-06
I don't know about pureftp, but vsftpd allows integration with your local account settings from which you can control access using Unix file permissions.

```
sudo aptitude install vsftpd
```

```
sudo gedit /etc/vsftpd.conf
```

Uncomment these lines...
```
local_enable=YES
write_enable=YES
chroot_local_user=YES
```

Change this line...
```
anonymous_enable=NO
```

To stop, start, or restart the server...

```
sudo /etc/init.d/vsftpd stop
sudo /etc/init.d/vsftpd start
sudo /etc/init.d/vsftpd restart
```

There is a directory called /home/ftp. I don't know what it's used for, maybe anonymous access.

On the client machine enter...
```
ftp 192.168.2.2 (or whatever the IP address of the FTP server)
```

Then enter your username/password. This is the local username/password you use to log into Ubuntu on the machine with the FTP server running on it. If you enter the ls command, you should see all the files in your home directory on the remote machine.

---

### Post by ojve on 2008-03-07
Thank you for your reply, but it was not really what I was looking for. Since pureFTP is in read only memory, I really don't want to mess with that and try to start a different server. Note that this is not Ubuntu, but some minimal version of Linux that I think migt be specific to D-link

//T

---

