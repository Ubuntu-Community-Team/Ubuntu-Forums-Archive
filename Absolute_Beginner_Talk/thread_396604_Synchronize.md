---
title: "Synchronize"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by jnorris235 on 2007-03-29
Many months of trying all sorts of methods - nothing will work!
I want to sync Laptop to NAS, then sync Desktop to NAS.
FTP works fine but you cant update cleverly.
Rsync, Grsync, Unison - all need to be installed at both ends I believe.

Laptop and NAS can see each other via Samba.
I was told how to update using Samba by using this:
sudo mount //192.168.2.2/jon  /tmp/test -t cifs -o username=jon,password=******,uid=jon,rw

All I get is >>Mount: Not a directory<<

Please help!

---

### Post by chili555 on 2007-03-29
Here is what I do, from linux to linux: ```
rsync &#8236;-a &#8236;-e ssh &#8236;--delete &#8236;/home/chili chili@&#8236;192.168.1.101:/home/bill/backup
``` ssh needs to be running on all machines, but rsync only on the machine issuing the command. It's a bit slow, so I start it at 11:00pm or so. If I were not lazy, I'd set up a daily cron job.

See man rsync, man cron and man woman.

---

### Post by huygens on 2007-04-03
> **jnorris235 said:**
> sudo mount //192.168.2.2/jon  /tmp/test -t cifs -o username=jon,password=******,uid=jon,rw

All I get is >>Mount: Not a directory<<

I guess this means that /tmp/test is not a directory.
The command you typed was requesting Samba to mount (meaning make local to tour computer) the shared directory jon (on 192.168.2.2) in the directory /tmp/test.
What did you intend to do? If you want to have the shared drive jon accessible to your laptop so you can copy files from your nas to your laptop and vice versa, then it is the correct path. I could recommend this post I wrote in the past: [http://ubuntuforums.org/showthread.php?p=1440697](http://ubuntuforums.org/showthread.php?p=1440697) it could help you understand more Samba.

N.B.: smbfs and cifs are pretty similar and cifs has some backward compatibilities with smbfs. So you could use my post and replace each occurrence of smbfs by cifs, or just leave it as is.

---

