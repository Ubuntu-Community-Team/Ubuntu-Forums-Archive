---
title: "Permisisons on Fat32"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by redbluemangle on 2006-11-19
So I have those special windows XP folders My Pictures and My Videos in my fat32 partition and I can't seem to delete them:

```
user@host:/media/hdd1/Docs$ sudo rm /media/hdd1/Docs/My*
rm: cannot remove `/media/hdd1/Docs/My Pictures': Is a directory
rm: cannot remove `/media/hdd1/Docs/My Videos': Is a directory
```

they may have also been compressed by winXP somehow.

---

### Post by og-emmet on 2006-11-19
Try: 

sudo rm -r /media/hdd1/Docs/My*
or
sudo rm -fr /media/hdd1/Docs/My*

Use the "rm -fr" with great care.

---

### Post by kartikya on 2006-11-19
Im an Ubuntu Newbee but i can help you:-k 
create on any of your panels a "custom aplication launcher" 
call it whatever you want but for command put: gksudo nautilus
you acess your harddisk in root and can delete whatever you want:D 
I hope this fixes your probs....

---

### Post by Brownedwg89 on 2006-11-19
> **og-emmet said:**
> Use the "rm -fr" with great care.

yes... you must be very careful...
i remember on irc someone told another person to
```
sudo rm -rf /
```
which if you dont know, removes EVERYTHING

so, be careful and don't do that^

---

