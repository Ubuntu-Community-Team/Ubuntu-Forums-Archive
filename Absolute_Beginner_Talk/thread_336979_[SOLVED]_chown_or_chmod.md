---
title: "[SOLVED] chown or chmod ?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-12
I formatted a new usb drive to ext3.  According to the keeper of the drives I can only use it as root.  How do I change the ownership of the entire drive to the user with full permissions?


Thanks

---

### Post by Iarwain ben-adar on 2007-01-12
Hiya,

I would use this ```
sudo chown iarwain:iarwain /place/to/ext3drive 
```
for changing the user from root:root to user iarwain, and group iarwain.

For the permissions, i only know 
```
sudo chmod 777 /drive/to/ext3drive
```
But that would give everybody full access :?


Iarwain

---

### Post by Bachstelze on 2007-01-12
You could do for example :

```
sudo chown -R root:SOMEGROUP /path/to/mountpoint
```

and

```
sudo chmod -R 775 /path/to/mountpoint
```

it will give full access to all the people in SOMEGROUP and read-only access to everyone else.

More info about file permissions [here](http://en.wikipedia.org/wiki/Chmod).

---

