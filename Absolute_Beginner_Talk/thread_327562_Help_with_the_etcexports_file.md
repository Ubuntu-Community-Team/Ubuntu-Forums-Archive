---
title: "Help with the /etc/exports file"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by ksinc on 2006-12-29
I have lots of experience managing Windows Domains but I am very new to Linux so I have setup a small (2 machine) network. I have a machine running the server version of Dapper Drake and a machine running the desktop version of Dapper Drake. I have installed NFS on the server and created a directory called share at the root of the hard drive. Now I want to share the directory by adding a an entry in the /etc/exports file so that I can access the directory from the desktop machine. I know the syntax is:

/share host1.mydomain.com(rw,sync,no_root_squash)

Is there a default domain? I don't remember specifying one while installing the server.

Is host1 the name of the desktop machine? How would I find that? Again, I don't remember specifying during the install.

Is there a wildcard that can be used to specify all machines?

Thank you.

Kevin

---

### Post by pseudonym on 2006-12-29
Sorry if this may seem a little 'RTFM' but have you checked out the [NFS Howto]("http://nfs.sourceforge.net/nfs-howto/")? It was updated this year so i think it should have all the info you need.

Just on using NFS, when I used it I found the transfer speed a little slow, and if you have a lot of stuff listed in your exports file it takes a long time to initialise. For simple file transfers between 2 PCs I found it a lot easier to just set up an ftp server on the non-gateway PC and use the gftp browser/transfer utility (it's in the Ubuntu repositories). 

But obviously if it's sharing you need then NFS is more suitable. Though I think these days people are moving to [Samba]("http://us4.samba.org/samba/") even for sharing between Linux PCs?

---

### Post by ksinc on 2006-12-29
Thanks for the response. I don't have any real need to use a particular method, I'm just trying to learn how all the aspects of Linux works. After reading that how to I'm not sure that the Desktop version of Dapper Drake supports NFS (at least I couldn't find it). 

Kevin

---

### Post by pseudonym on 2006-12-29
> **ksinc said:**
> Thanks for the response. I don't have any real need to use a particular method, I'm just trying to learn how all the aspects of Linux works. After reading that how to I'm not sure that the Desktop version of Dapper Drake supports NFS (at least I couldn't find it). 

Kevin
Its supported in Dapper - NFS has been around for years. However, silly me probably should have pointed you [here]("http://www.ubuntuforums.org/showthread.php?t=249889") as well :confused:
Once you're set up you should go back to the security section of the original NFS Howto to learn how to secure the portmap daemon via the /etc/hosts.allow and /etc/hosts.deny files.

HTH :)

---

