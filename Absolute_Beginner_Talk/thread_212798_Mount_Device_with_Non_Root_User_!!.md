---
title: "Mount Device with Non Root User !!"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by widjaja31 on 2006-07-10
how to mount a device without non root user ?
i try this statement :
  mount -t smbfs //server/sharename /data
and it said only root can do mount !!

btw i also try to mount samba network driver automatically when a user login. i add this line into /etc/fstab

//server/sharename /data smbfs defaults 0 0

but it still not Work !!

Please someone help !!

Thanx
Ronny

---

### Post by bocmaxima on 2006-07-10
try

sudo mount -t smbfs //server/sharename /data

---

### Post by widjaja31 on 2006-07-11
I mean non Root user. if u use Sudo, that's mean u use root user. 
one thing that i ask is how to make my non root user ( for example : linda user ) can mount a device but linda isn't a root user ??
thanx

---

### Post by bocmaxima on 2006-07-12
> **widjaja31 said:**
> I mean non Root user. if u use Sudo, that's mean u use root user. 
one thing that i ask is how to make my non root user ( for example : linda user ) can mount a device but linda isn't a root user ??
thanx

I thought sudo was one shot superuser, meaning not logging in as root, but allowing to do a command as root.

---

### Post by Brunellus on 2006-07-12
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

sudo gives limited superuser privileges for only one command at a time.  

root is a user with superuser privileges *all the time*.

---

