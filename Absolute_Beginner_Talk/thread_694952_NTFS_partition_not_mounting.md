---
title: "NTFS partition not mounting"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-02-12
I am having trouble getting my vista ntfs partition to mount automatically. It used to work but now it no longer works. The line below is what was in the fstab file while it was working:

/dev/sda1 /media/disk ntfs-3g defaults,nls=utf8,umask222 0 0

Now, when I use this line in fstab, the icon for the ntfs drive doesn't appear in the "My Computer" section. 

Can someone give me a new fstab line to use? This is what I want...
I want the partition to automatically mount and I want read/write access to it with needing sudo.

Also, if possible, I want to restrict the read/write access to my username if possible.

---

### Post by taurus on 2008-02-12
Maybe because you didn't shutdown your windows cleanly.  I bet that is what you'd get, from the error message, if you try to mount it by hand from a terminal.

Applications -> Accessories -> Terminal
```
sudo mount -t ntfs-3g /dev/sda1 /media/disk
```

---

### Post by MaindotC on 2008-03-10
I had the same issue and it was because I yanked out the power cord when I was in Winblows.  I restarted, logged into Winblows, shutdown, now I'm in Gutsy and I'm good :)  Thank you!

---

