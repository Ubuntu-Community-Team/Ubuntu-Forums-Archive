---
title: "Strange errror when trying to mount"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Mark Raymond on 2007-07-17
I'm still struggling to get my Windows share to mount properly.
I now have this in my fstab file:

//192.168.2.3/Mark /home/markr/mydocs smbfs user,noauto	0	0

but when I type:

mount //192.168.2.3/Mark

it comes up with:

smbmnt must be installed suid root for direct user mounts (1006,1006)
smbmnt failed: 1

I know that all the address are correct because this works:

sudo mount -o rw,user=markr //192.168.2.3/Mark /home/markr/mydocs

however it changes the owner to root so I can't access it fully.
For that matter why does it change the owner to root? And what does my error message mean?

---

### Post by kidders on 2007-07-18
Hi there,

Mounting filesystems has the potential to cause a great deal of damage both to your system, and the one that owns whatever is being mounted, so Linux doesn't grant normal users any privileges either to mount filesystems or access mounted filesystems without being explicitly instructed to do otherwise.

There are two things going on in your case...

> **Mark Raymond said:**
> sudo mount -o rw,user=markr //192.168.2.3/Mark /home/markr/mydocsAs you know, **mount** will use the access privileges of the user running the command, by default. Strictly speaking, this command *should* fail, since the remote host really ought to reject attempts to mount Samba shares as root, for security reasons. Also, note that although the "user" mount option exists, it doesn't take any arguments, so "user=markr" won't do anything. (See **mount**'s & **smbmount**'s man pages.)

> **Mark Raymond said:**
> smbmnt must be installed suid root for direct user mountsThis message means exactly what it says. In order to do its work, **smbmount** (a tool invoked by **mount** to handle Samba shares) needs root privileges, which means no normal user can (by default) execute it successfully. The way around that is to set **smbmount**'s SUID bit.

**A brief note:**
[SIZE=1]Setting a binary's SUID bit is, in general, _absolutely not recommended_ unless your box is used excusively by trusted users. You may notice that **mount**'s SUID permission is set on your system...```
# ls -l `which mount`
-rws--x--x 1 root root 116712 Jul  9 22:29 /bin/mount
```...allowing anyone who executes it to acquire root privileges unchallenged. I suppose the logic behind *not* automatically setting it in **smbmount**'s case is that the command has the potential to affect systems other than your own, making the security implications that little bit more significant.

[SIZE=2]Anyhow, I hope that answers both your questions.
[/SIZE]
[/SIZE]

---

