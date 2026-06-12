---
title: "backup with permissions"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by mgvbstar on 2007-06-27
Hello.  I am running feisty and I want to back up some files by tarring and copying the tarball to my other computer ( a windows machine).  My windows fs doesnt support permissions (its ether fat32 or ntfs-i cant remember). If I tar with the -p option and copy to my windows system, then copy the tarball back to ubuntu and untar, will my files still have the same permissions? Thanks

---

### Post by PCFascist on 2007-06-27
It looks like MS has the answer to this:
>  if your SAMBA domain and Windows Domain are same - you can
use xcopy command/backup on the Windows system to copy files from the
SAMBA share and reatin ownership/permissions. 

More from the same post:
> What user you ran the tar command as? root? Was root mappped to an
Administrator on the Windows domain?
Did you try using the cp command with -p switch?

Here's a test you should give a try -
- Create 3-4 files on SAMBA Server
- Change the users/groups on them so now the files have different
owners like root, user1, user2 etc
- Ensure that you map these same users to valid Windows domain
accounts. Map root to a domain admin account.
- Create a folder on Windows system running Server for NFS. Add
Anonymous Logon group and Domain Admin account and give them full
control.
- Share this folder from Windows server over NFS - Allow Anonymous
access, Allow root access, ALL MACHINES Read-Write
- Mount this share on your SAMBA server
- Run this command - cp -p /localdir/* /nfsmount/*
- After the copying is done, check if it retains the ownerships. If it
does, try the tar command again. 

[http://www.microsoft.com/communities/newsgroups/en-us/default.aspx?dg=microsoft.public.servicesforunix.general&tid=5e0ffb1c-f637-4e28-8784-2461192b2216&p=1](http://www.microsoft.com/communities/newsgroups/en-us/default.aspx?dg=microsoft.public.servicesforunix.general&tid=5e0ffb1c-f637-4e28-8784-2461192b2216&p=1)

---

