---
title: "mounting a remote file system"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by jo2 on 2005-12-24
Hi,

I'm an absolute beginner in networking on linux (ubuntu 5.04).
I am trying to share my files using Samba.
I can already mount a remote file system using
sudo mount -t smb //mercurius/R /media/C_on_Mercurius 
(the computer then asks me for a password, so I type my root password).
This works

Now I am trying to mount the remote filesystem automatticaly on start-up:
I have added to /etc/fstab the following line:
//mercurius/R   /media/C_on_Mercurius   smbfs   password=(root password),fmask=755,dmask=755     0       0
On start-up I get the message that acces was denied.
What am I doing wrong?
Thanks
Jonas

---

