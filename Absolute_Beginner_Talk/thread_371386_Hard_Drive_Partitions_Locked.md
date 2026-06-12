---
title: "Hard Drive Partitions Locked"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by absoluthamm on 2007-02-26
I was just trying to go through and actually install 6.06 from my LiveCD and for some reason there is a little lock next to both partitions that I have when I get to the partitioning part in the installation. I also am not allowed to read my partitions through the File Manager, but they show up. When I click on the folder, it tells me that I do not have the correct permissions to open it. How is it that I can change these permissions? I have installed 6.06 successfully twice on my laptops and never ran into this. I am assuming that I have to change some setting in WinXP(yes it's a dual boot), but I am not sure what one. I searched through the forums for a while and didn't find anything, so thanks a lot in advance.

AbsolutHamm

---

### Post by taurus on 2007-02-26
Do you mount your Windows partition, ntfs, through /etc/fstab or do you mount it by hand?  If you mount it through /etc/fstab, can you post it here?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by absoluthamm on 2007-02-26
I didn't have to mount it, I went to System>Admin>Disks and I was going to click enable on the partitions I wanted to mount, but they were already enabled. This is what the Official Documentation says to do. I did what you said with the cat /etc/fstab and this was my output:
```

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$

```

---

### Post by taurus on 2007-02-26
So you want to access your Windows partition from the LiveCD!  What's the output of this command from a terminal?

```
df -h
```

---

### Post by absoluthamm on 2007-02-26
Well, I would like to be able to access some files from the Windows partition later on, but my main problem is that I am unable to partition my HD right now into a Linux partition because when I go through the setup process, I am getting a little lock icon next to the partition names.

Here is the output from df -h:
```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.2G  688M  441M  61% /
varrun                506M   76K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  212K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  8.8M  497M   2% /lib/modules/2.6.15-23-386/volatile
tmpfs                 506M   20K  506M   1% /tmp
/dev/hda1             128G   77G   52G  60% /tmp/disks-conf-hda1
/dev/hda2              59G   39G   20G  66% /tmp/disks-conf-hda2
ubuntu@ubuntu:~$

```

---

### Post by absoluthamm on 2007-02-26
here is a screenshot of what i am talking about .

[IMG]http://i179.photobucket.com/albums/w282/absoluthamm/partition.png[/IMG]

---

