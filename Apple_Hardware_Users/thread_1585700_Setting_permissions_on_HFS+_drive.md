---
title: "Setting permissions on HFS+ drive"
date: 2010-09-30
forum: Apple Hardware Users
---

### Post by Leopoguin on 2010-09-30
Hi all,

If I mount an HFS+ drive to my filesystem and change permissions on that drive, are the permissions changed only within Linux, or would different operating systems also see the changed permissions?  In my case I'm dual booting a Mac Mini.  The stock install doesn't give me permissions to read/write to my HFS+ partition.  I'm wondering if I change the permissions, will they be screwed up next time I boot into OS X? Thanks for any help.

---

### Post by linuxopjemac on 2010-10-01
It should be for all systems able to read that partition.

---

### Post by srs5694 on 2010-10-01
In most cases, the best solution to this problem is to synchronize your user ID (UID) and group ID (GID) values between the two dual-boot OSes. Chances are you only need to change the UID and GID values for one user -- namely your login account. You can do the job with the text-mode usermod command or with some GUI front-ends to it. For instance:

```

sudo usermod -g 1023 -u 1234 fred

```

This changes fred's GID to 1023 and UID to 1234. You'll need to figure out what values to use based on the UID and GID used in OS X.

Once you do this, though, fred will no longer own the files previously owned in Linux. You'll need to use chown to overcome this problem. The following should do the job for most of the files:

```

sudo chown -R fred: /home/fred

```

If fred has created files in other directories, you'll have to track them down and change them, too.

It's best to do this from a pure root login, but Ubuntu doesn't support this by default, so you should shut down everything you don't need, run those commands, log out, and log back in again. If you have problems at that point, you'll need to use an emergency disc to recover.

Another option is to create an entirely new account, setting the UID and GID values to match those used by your main account in OS X. You'd then abandon your current Ubuntu account, copying files as necessary and then deleting the old home directory tree. This approach is probably a bit safer, but it's more hassle unless something goes wrong with the first method.

Alternatively, you can leave the Ubuntu settings alone and change the values in OS X. In principle, the process is the same; however, I don't know offhand if OS X supports usermod and chown in precisely the same way as Ubuntu does.

---

### Post by Leopoguin on 2010-10-02
> **srs5694 said:**
> 
Alternatively, you can leave the Ubuntu settings alone and change the values in OS X. In principle, the process is the same; however, I don't know offhand if OS X supports usermod and chown in precisely the same way as Ubuntu does.

Thanks, I'll try to change it in Ubuntu. OS X doesn't have usermod (probably there is some equivalent, don't know what).  It does have the more common chown.

---

### Post by maxbucknell on 2010-10-02
I'm unsure about this. I have an external hfs+ drive, that my linux has no permission to read or whatever, but snow leopard can do everything on. I was unable to change the permissions for it in linux because there was no owner and not even root could own it. So I booted into an OS X dvd and changed the permissions there, which worked fine.

Still no change when I booted back though.

[tl;dr start here]
I believe the reason I had access in OS X is because Apple only uses unix file permissions to a point. For anything more tailored, it does its own thing.

I guess it should work, but it might not necessarily.

---

### Post by linuxopjemac on 2010-10-03
This thread can be handy:
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=95)

---

