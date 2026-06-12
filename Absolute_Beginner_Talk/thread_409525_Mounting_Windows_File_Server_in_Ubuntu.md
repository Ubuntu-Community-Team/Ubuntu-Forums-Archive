---
title: "Mounting Windows File Server in Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-14
OK, I've been going through the forums and wikis and everything I find says something different, and nothing works.  

I have a files server running Windows XP.  I have Samba set up to the extent that I can access those files through "Network Server".  I would like to permanently mount my network WIndows server disk in Ubuntu so that it acts like part of the linux file system (i.e. in the /mnt/share directory) so I can use programs on the Ubuntu box that ask for directories but won't search for network files.  Does this make sense?  

Thanks.

---

### Post by kc5hwb on 2007-04-14
I am new to Ubuntu also and I don't wanna go talking out of my ***, but you *should* be able to mount it this way....


```
mount -t smbfs -o gid=<group>,uid=<username> netpath mntpoint
```

You might not need that gid and uid part, since your share is on a XP box.  But this line worked for me, mounting a network share onto my local machine, thru SAMBA, from another Ubuntu box.

---

### Post by thefoolisme on 2007-04-14
> **kc5hwb said:**
> 

```
mount -t smbfs -o gid=<group>,uid=<username> netpath mntpoint
```



OK, I'm not sure how to use the code.  Is gid the network name (i.e.MSHOME), and user name would be my samba user name?  Where do I put in the same of the server (AMDServer) and folder (Music_Movies) I want to permanently mount?  

Thanks.

---

### Post by thefoolisme on 2007-04-15
If someone could explain to me in simple language how to permanently mount my Windows Files Server disk, I would really appreciate it.  Every post, wiki, and document I read says something slightly different, and I can't get it to work.  

Thanks.

---

### Post by vanadium on 2007-04-15
The Ubuntu Wiki has this information on permanently mounting a Windows share:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

Did you already see it? Taylored for Ubuntu, it should work.

---

