---
title: "Possible to change ownership on whole partition at once? [Resolved]"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-04-27
Is it possible to change the owner of a whole partition of files from root to a certain user in one go? Or do you have to change every file individually?

---

### Post by Bachstelze on 2007-04-27
```
sudo chown -R foobar /mnt/something
```

will change the owner of /mnt/something as well as everything that's below it to user foobar.

---

### Post by trishacupra on 2007-04-27
Is this correct to change the owner of a partition mounted in media/Work to the user - trisha?

**sudo chown -R trisha /media/Work**

---

### Post by Bachstelze on 2007-04-27
Yes, provided that the filesystem used support permissions (i.e. not FAT32 or NTFS).

---

### Post by aysiu on 2007-04-27
One of these should help you out:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

