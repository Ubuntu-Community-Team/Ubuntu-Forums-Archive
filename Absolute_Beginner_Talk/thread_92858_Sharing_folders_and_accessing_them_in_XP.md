---
title: "Sharing folders and accessing them in XP"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Falklian on 2005-11-20
Just installed Ubuntu on a spare computer, trying to set up file sharing.  Post-install, I could access all shard folders on my XP machines.  I set up Samba and shared a folder but when I try to access it, it asks for a username/password and everything I type in gets rejected.  Is there any way to not require a username/password when browsing shared folders on my Ubuntu machine?

---

### Post by apjone on 2005-11-20
in terminal

sudo apt-get samba
sudo apt-get smbfs
sudo smbpasswd -a username

then enter a password

-a enables  username
-d disables   ----"--------

---

### Post by Falklian on 2005-11-21
Thanks!  That worked fine for my Windows machines, but now I have another problem.  For some reason, my Ubuntu machine cannot see my Windows machines and I can't even manually mount shares in Ubuntu.  Any insight?

---

### Post by xelink on 2005-11-21
can't you just make a fat 32 partition? I did that and it seems fine to me. I am a beginner though so...

---

### Post by Wes24 on 2005-11-21
You should be able to mount NTFS partitions as well. Maybe the following link can help you:
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by Falklian on 2005-11-21
I have 5 computers, Ubuntu is on one seperate computer, just trying to access the shared folders that are on the Windows machines.  I was able to access them last night when I set Ubuntu up, today though, I could not access them from my Ubuntu machine.  The XP machines see the Ubuntu shares fine though.

---

### Post by casper_2095 on 2005-11-21
Are you looking for smbclient?
```

$ smbclient //somemachine/someshare
smb/> ls

$ man smbclient
       smbclient  is  a  client  that  can  &#8217;talk&#8217;  to  an SMB/CIFS server. It offers an interface similar to that of the ftp program (see
       ftp(1)). Operations include things like getting files from the server to the local machine, putting files from the local machine to
       the server, retrieving directory information from the server and so on.

```

---

