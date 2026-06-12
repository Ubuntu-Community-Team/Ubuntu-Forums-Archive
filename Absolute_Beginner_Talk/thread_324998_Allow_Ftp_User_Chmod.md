---
title: "Allow Ftp User Chmod"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by EneWolverine on 2006-12-24
Hi all,

I've been trying to scourge the net for the last few hours trying to fix a problem I'm having with my proftpd server.

I've managed to setup my ftp server fine. I created a login account and I can get into the ftp server without any probs. I've been able to setup nearly all the permissions for the ftp user as well i.e. add files, delete files, overwrite files.

For some reason tho with this user I can't change permission files with CHMOD. I get a 550 error saying Permission Denied.

I looked up how I could allow chmod and found out that if I add SITE_CHMOD to LIMIT that I should be able to change file permissions.

However this doesn't seem to be working

I restarted my ftp server as well and even rebooted the system.

Still no luck.

Everything else is working except this. 

If anyone here has a solution I would really like to hear from you.

Thanks in advance,

The Wolverine :D

---

### Post by EneWolverine on 2006-12-25
Still looking for a solution to this.

I've managed to figure out that it's basically files owned by root that my ftp user can't chmod. I can delete these files tho. And I can also chmod files that I upload under my ftp user account.

So I think somehow my ftp user hasn't inherited all the rights that root has. 

Anyhow thoughts on how I could go about giving the ftp user the right to chmod files owned by root would be great. I think it's a simple user account management issue; my knowledge of such user management in UNIX is still limited.

The Wolverine :D

---

