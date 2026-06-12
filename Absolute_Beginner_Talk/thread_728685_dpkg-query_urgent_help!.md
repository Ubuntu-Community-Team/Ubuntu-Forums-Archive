---
title: "dpkg-query urgent help!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2008-03-19
dpkg-query: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

I can't run anything apt-get related.
Please help!  I can't install or remove any packages.

---

### Post by forestpixie on 2008-03-19
try 
```
sudo apt-get install -f
```

if you get the same error
```

ls /var/lib/dpkg
```

if there's an old one you could try renaming the file after making a backup - but not too sure
```

sudo cp /var/lib/dpkg/available /var/lib/dpkg/available.bak
sudo mv /var/lib/dpkg/available-old  /var/lib/dpkg/available 
sudo apt-get update

```

---

### Post by chris062689 on 2008-03-19
Neither of those worked.
chris@eeepc:~$ ls /var/lib/dpkg
alternatives  diversions-old  parts             status      updates
cmethopt      info            statoverride      status-old
diversions    lock            statoverride-old  triggers
The following are in blue: alternatives, parts, updates, info, triggers

---

### Post by glennric on 2008-03-19
Try
```
sudo dpkg --clear-avail
sudo apt-get update
```

---

