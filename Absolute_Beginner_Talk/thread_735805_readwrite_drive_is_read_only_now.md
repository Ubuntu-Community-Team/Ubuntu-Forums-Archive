---
title: "read/write drive is read only now"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by PeterRedford on 2008-03-26
okay I have 1 60GB hard drive that I had portioned 3 ways. 20 xp 20 ubuntu and then 20 gig for transferring stuff back and forth and for downloading stuff to.

all of a suddon it has switched to a read only drive. I have no idea what I was doing that made it turn into a read only drive.

how can I switch it back to read/write. 

it just says I do not have permission to do anything in the drive.
I can delete stuff in it with XP but I never use xp anymore so I dont really want to have to switch back just to do that.

---

### Post by zen_waters on 2008-03-26
So did you format the drive with NTFS?  Know that most distros of linux don't write directly to NTFS Windows partitions.

---

### Post by PeterRedford on 2008-03-26
no its vfat.
I can still write to it. but I cant delete stuff from it unless I switch to xp.

---

### Post by jan quark on 2008-03-26
please post the result of these terminal commands

```
sudo fdisk -l
cat /etc/fstab
```

to change the permissions do this:
```
sudo chown -R usr:usr CU

sudo chmod -R 755 CU
```

and change usr:usr to your user name for instance bob:bob
and CU change to the ```
/path/to/folder/or/partition 
```

---

