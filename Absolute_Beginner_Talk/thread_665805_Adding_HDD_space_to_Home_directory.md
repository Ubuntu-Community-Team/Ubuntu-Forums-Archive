---
title: "Adding HDD space to Home directory"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2008-01-12
My Home directory is at 100%. I wish to allocate more space to it. I have a 43GB disk formatted as ext3 which Ubuntu can mount. Is it possible to allocate this disk space to my Home directory and if so, how? 

Output of df -h is as follows:
```
charles@charles-desktop:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              44G   44G     0 100% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   96K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             102G   50G   47G  52% /home
/dev/sda1              66G   29G   38G  44% /media/sda1
overflow              1.0M  372K  652K  37% /tmp
/dev/scd0             233M  233M     0 100% /media/cdrom0
/dev/sdb2              46G  181M   44G   1% /media/disk
charles@charles-desktop:~$ 

```

---

### Post by Dr Small on 2008-01-12
I see your /home directory as 52% used instead of 100%.
Your / directory is the one that is 100% used.

Dr Small

---

### Post by PeterJS on 2008-01-12
It's your root file system that is full not your home directory. You might want to run the baobab disk space analyzer to figure out what's taking up all that space, and if you can move it to somewhere more convenient like that extra disk.

---

### Post by dcstar on 2008-01-12
> **PeterJS said:**
> It's your root file system that is full not your home directory. You might want to run the baobab disk space analyzer to figure out what's taking up all that space, and if you can move it to somewhere more convenient like that extra disk.

It amazes me that someone with a separate /home directory can fill up a 44G root directory, there must be some misbehaving applications storing files there.

Anyhow, the short-term fix will be to find where these apps are storing the files and create some soft links to the /home partition (and move the data there).

---

