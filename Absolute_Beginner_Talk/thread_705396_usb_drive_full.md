---
title: "usb drive full ???"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2008-02-23
I have a problem that's driving me nuts.  I'm trying to d/l a large file (29gigs) to my usb drive.  It's formatted in ext3, but Deluge tells me the drive is full.  It's a 250 gig drive with about  140 gigs free...any thots ?? Is there a limit on partition size in Gutsy or something I missed ??
Thanks ; )

---

### Post by taurus on 2008-02-23
What's the output of this command from a terminal?

```
df -h
```

---

### Post by MrKlean on 2008-02-23
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  6.6G   94G   7% /
varrun                1.2G   96K  1.2G   1% /var/run
varlock               1.2G     0  1.2G   0% /var/lock
udev                  1.2G   84K  1.2G   1% /dev
devshm                1.2G     0  1.2G   0% /dev/shm
lrm                   1.2G   38M  1.1G   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             230G  101G  117G  47% /media/My_Book

the last one is the one I'm trying to d/l to.  Looks like there's plenty f room ; (

---

### Post by MrKlean on 2008-02-23
any help ??

---

