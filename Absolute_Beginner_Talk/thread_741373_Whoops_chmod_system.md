---
title: "Whoops chmod system"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Holmes89 on 2008-03-31
I think I may have messed something up and don't know how to fix it, I was working on sharing a folder on a FTP server so I had the users linked to the same folder and it worked the only thing was they could not upload or download to it. So I went to change file permissions and so I set the directory to /home/ ( the folder was  subfolder called /netshare/) so I typed in 

sudo chmod +rw /netshare/ 

and it didn't work I then tried 

sudo chmod -R 664 netshare

now the ftp server can access every folder, what can I do to fix this? I only want them to be able to read an write to /netshare/

---

### Post by Inxsible on 2008-03-31
it should be ```
sudo chmod +rw /home/netshare
```since you said netshare is a subfolder of home

---

### Post by cmnorton on 2008-03-31
How you could have set the protections on these directories depends on whether the ftp users accessing files in netshare are part of a group or just random users:

You could do

chmod -R 700 /netshare
chmod 777 netshare, and the lower directories should remain unreachable.

---

### Post by Holmes89 on 2008-03-31
did I mess something up with my system though? is there something I need to fix?

---

### Post by Holmes89 on 2008-03-31
> **Inxsible said:**
> it should be ```
sudo chmod +rw /home/netshare
```since you said netshare is a subfolder of home

but I was in the home directory

cd home

---

### Post by Inxsible on 2008-03-31
> **Holmes89 said:**
> but I was in the home directory

cd home
aah ! I didnt catch that. Sorry

---

### Post by Holmes89 on 2008-03-31
> **cmnorton said:**
> How you could have set the protections on these directories depends on whether the ftp users accessing files in netshare are part of a group or just random users:

You could do

chmod -R 700 /netshare
chmod 777 netshare, and the lower directories should remain unreachable.

Okay I think that works but they can still get to other places and download things how can I fix that? Does this have to do with the thing I did earlier?

---

### Post by cmnorton on 2008-04-01
First each ftp server is configured a little differently. I use vsftpd, and googled for 

restricting vsftpd access

and found a bunch of different links, most of which were fairly useful. 

Here is one:

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/47425-vsftpd-how-do-i-restrict-access-users-home-dirs.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/47425-vsftpd-how-do-i-restrict-access-users-home-dirs.html)

Most of these configuration changes will be in the ftp servers configuration file. vsftpd's is in /etc/vsftpd.conf

---

