---
title: "mounting ext3 partion"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by group1 on 2007-03-21
ok i have ubuntu 6.10 installed. i added  /dev/hda1 /media/main ext3 rw,user

it mounts the drive on boot no problem and if i'm root everything is fine. But i don't want to be root all the time. How do I make it writable with other users


thank you

---

### Post by phiphedog on 2007-03-21
You could try adding a umask to the command 

dev/hda1 /media/main ext3 rw,user "umask=002"

or change the permissions on you /media/main folder
chmod -R 775 /media/main

---

### Post by taurus on 2007-03-21
You just change the ownership of  /media/main from root to your login name.  Assuming your login name is **john**, open a terminal and do

Applications -> Accessories -> Terminal
```
sudo chown -R **john**:**john** /media/main
ls -la /media
```

p.s.  You may want to change the entry for /dev/hda1 in /etc/fstab to look like this.

```
/dev/hda1   /media/main   ext3  defaults   0   1
```

---

### Post by group1 on 2007-03-22
thanks a lot, that seemed to work changing permission on /main

---

### Post by esaym on 2007-03-22
Does ubuntu not have a manager for this like Kubuntu?

---

