---
title: "New User"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by xrayman55 on 2008-04-08
Hi  

I have a 9 year old who is an IT Geek and proud of it.  He has installed ubuntu server software on to a PC wants to get 2 lap tops sharing documents.  My question to you ubuntu guros out there can you help a Dad help his son to accomplish his goal

Thanks

:)

---

### Post by Oldsoldier2003 on 2008-04-08
> **xrayman55 said:**
> Hi  

I have a 9 year old who is an IT Geek and proud of it.  He has installed ubuntu server software on to a PC wants to get 2 lap tops sharing documents.  My question to you ubuntu guros out there can you help a Dad help his son to accomplish his goal

Thanks

:)

If the laptops wont be running Ubuntu then the thing to do is have him install samba on the server. Alternatively you could google and look for the windows drivers that allow you to read and write t ext2/3 partitions, but I think for the learning value Setting up a samba server would be more fun and productive.

besides that, I just dont trust the stabilty of windows enough to allow it to write to linux partitions. :)

---

### Post by tamoneya on 2008-04-08
you could also look into install a ssh/scp server.  Its pretty simple```
sudo apt-get install ssh
```
Then in nautilius just type ssh://IP.AD.DRE.SS/ and you should be able to view files on the ssh server.  You will need to log in with the user name and password for the server though.

---

### Post by bodhi.zazen on 2008-04-08
for file sharing (documents) your options are :

NFS, Samba, FTP, HTTP, and sshfs (ssh with ssh mount or scp).

Of these protocols I second Samba, It is fairly easy and secure.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Over time I suggest you look at ssh as it is very fun as well :

[uwiki]SSHHowto[/uwiki]

sshfs :

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)
	[http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/)


NFS is easy to set up, but less secure then samba.

FTP is easy to set up and there are graphical interfaces (gftp), but be sure to secure it (ie install vsftp).

HTTP (apache) is fun too, but obviously a little over kill.

---

