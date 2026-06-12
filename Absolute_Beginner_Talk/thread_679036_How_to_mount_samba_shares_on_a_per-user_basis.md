---
title: "How to mount samba shares on a per-user basis?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bentob0x on 2008-01-26
Hi

The problem I have is very simple: I want to mount different samba network shares for different users using different credentials.  

If I mount the shares in /etc/fstab, they will be available to everybody (with or without credentials).

Obviously, having something along the way of a /home/username/.fstab file would be a security threat as it would mean that any user could mount filesystems and you don't want that (which is probalby the reason why it's not implemented already in the filesystem).

Does a 'mount-a-network-share-per-user' centralised system exists?

Thank you for your help.
- bento

---

### Post by gerscht on 2008-01-26
SMB for fuse might be the one you're looking for. [http://www.ricardis.tudelft.nl/~vincent/fusesmb/](http://www.ricardis.tudelft.nl/~vincent/fusesmb/)
There are also scripts to mount with KDE startup [http://linux.bononline.nl/linux/sessionscripts/02/example02.php](http://linux.bononline.nl/linux/sessionscripts/02/example02.php)

If you only have a couple of shares, it might be worth putting them in /etc/fstab anyways, and setting the owner:group to the specific accounts only. This will help you to keep the data central
```
/network/path /mount/point smbfs user,credentials=/etc/samba/cred-file,uid=YOURUSER,gid=YOURGROUP,fmask=0770,dmask=0770 0 0
```
'user' in options will make it mountable by standard users, not root only

---

### Post by dcstar on 2008-01-26
> **bentob0x said:**
> Hi

The problem I have is very simple: I want to mount different samba network shares for different users using different credentials.  

If I mount the shares in /etc/fstab, they will be available to everybody (with or without credentials).

Obviously, having something along the way of a /home/username/.fstab file would be a security threat as it would mean that any user could mount filesystems and you don't want that (which is probalby the reason why it's not implemented already in the filesystem).

Does a 'mount-a-network-share-per-user' centralised system exists?

Thank you for your help.
- bento

I can open a share with the following command:
```
smb://computer/share
```
Why not put that sort of thing in each individuals System-Sessions-Preferences-Startup Programs to make the connection when they log in?

You can even try the ```
smb://username:password@server/share
``` to see if it logs in automagically.

---

