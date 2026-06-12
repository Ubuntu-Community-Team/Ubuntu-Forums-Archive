---
title: "Need help with patition access!"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Escozz on 2007-04-11
Hey all. i am running ubuntu 6.10 and i have made a special partition to have my music, videos, etc. on. but i can't access it from my user account. i can only access it as root. and i would like to know how i change that.

And since i am new to Ubuntu i would be really happy if you could give me a step by step guide :KS 


thanks for your help.

p.s 
Sorry if my English is bad

---

### Post by taurus on 2007-04-11
What filesystem is that partition and where do you currently mount it?  If it is ext3, then you can change the ownership from root to your login name so you can read to it whenever you want.

---

### Post by Escozz on 2007-04-11
this is what i know about the partition hope this info is good enough

format:ext3
name:hdb1

So how do i change the ownership to my login name?

---

### Post by taurus on 2007-04-11
Where do you mount /dev/hdb1?  Can you post the following commands from a terminal here?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
id
```

---

### Post by DoubleQuadword on 2007-04-11
I'm assuming your **hdb1** is mounted somewhere (like /media/hdb1), if that is the case, you can try two things (both as 'root' user):

First, in a terminal type the following:

```
sudo chown <your_user>:<your_group> <mount_dir>
```

This should work; now, if for some reason it does not try this:

* Go to System >> Administration >> Login Window >> Security (tab) and check the "Allow local system administrator login".
* Logout and login again as root (from the login window).
* Look for the folder where your **hdb1** is currently mounted.
* Modify its access right/s in order to suit your needs.

Eventually, you'll end up having the access permission needed.

Regards.

---

### Post by Escozz on 2007-04-11
Thanks for the help everybody i finaly got access to my partition :)

---

### Post by DoubleQuadword on 2007-04-11
> **Escozz said:**
> Thanks for the help everybody i finaly got access to my partition :)

You're quite welcome.

---

