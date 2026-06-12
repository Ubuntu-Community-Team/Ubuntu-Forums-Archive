---
title: "Mounting a Mac folder on Ubuntu using SMB and fstab"
date: 2011-11-27
forum: Apple Hardware Users
---

### Post by Untitled_No4 on 2011-11-27
Hi,

I'm trying to mount a shared Mac folder (using SMB) on Ubuntu via fstab and I get the following error:
```
mount error(22): Invalid argument
```

in fstab I have the following line:
```
//192.168.0.101/Web  /media/test cifs credentials=/etc/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777  0  0
```

If I change the server to reflect an SMB shared folder on Ubuntu it does work.

If I open dolphin and enter smb://192.168.0.101/Web I am prompted to enter my username and password and can access the share, but I want it mounted on automatically on startup.

Does anyone have an idea how I can mount a network-shared Mac folder on Ubuntu?  Is it even possible?

Thanks.

---

### Post by Untitled_No4 on 2011-12-03
Apparently the problem is with MacOS Lion that uses SMBX instead of Samba. Anyway, I managed to find a solution, which I am including here for future refernece.

If you want to mount the folder using command line you need to run:
```
sudo mount -t cifs //server/folder -o 'crednetials=credentialsfile,rw,nounix,noserverinfo,sec=ntlmssp' /path/to/local/folder
```

and in fstab you should have:
```
//server/folder   /path/to/local/folder cifs credentials=credentialfile,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,nounix,noserverinfo,sec=ntlmssp 0 0
```
While this doesn't mount the folder when running "sudo mount -a" (it says permission denied), it does mount the during boot process.

Hope this helps someone, somewhere.

---

### Post by Untitled_No4 on 2011-12-03
One last note: This solution is right for Ubuntu 11.11. Future versions of the Linux Kernel will apparently include support that will allow the old syntax to work, so try this first if you are visiting this page from the distant future.

---

### Post by jamessnell on 2013-02-19
-- REMOVED COMMENT: I complained it wasn't working for me, when I merely had my head stuck up my ****--

---

### Post by codemaniac on 2013-02-19
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old.

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thread closed.

Thanks!

---

