---
title: "giving full permissions to a shared folder"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by bduenskie on 2006-10-30
Hey all,

I've setup the following share via NFS:
/var/www 192.168.1.1/24(rw,no_root_squash,async,insecure)

I'm accessing it via a mounted drive on my iMac.

How do I setup the share to give full permissions, I see I have "rw", which gives me read and write, but what else can I allow?  How do I set it up so sub-directories can be created, I want to give full access to the share.

Thanks

---

### Post by bodhi.zazen on 2006-10-30
See if this helps you: [How to NFS](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by bduenskie on 2006-10-31
I followed those instructions for my setup which worked just fine. However I can't seem to create folders, do I need to modify the permissions here:

/var/www 192.168.1.1/24(**rw**,no_root_squash,async,insecure)

Or is rw the most I can give to the share?

---

### Post by bduenskie on 2006-10-31
Would this work, changing this:

/var/www 192.168.1.1/24(rw,no_root_squash,async,insecure)

to this:

/var/www 192.168.1.1/24(rw**x**,no_root_squash,async,insecure)

---

