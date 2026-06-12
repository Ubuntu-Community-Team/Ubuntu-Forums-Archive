---
title: "fstab/ntfs-3g problem"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by HarryM on 2007-10-31
I might be doing something stupid, but I can't see the problem, whatever it is.

I have three NTFS drives in a system running Gutsy. I've successfully set two of them up ("archive" and "windows") to mount how I'd like them, which is owned by arta:users with files as rw and directories as rwx:

```

root@arta-serv:/mnt# ls -l
total 20
drwxrwx--- 1 arta users  4096 2007-10-31 16:31 archive
drwxrwxrwx 1 root root   4096 2007-10-11 14:13 spare
drwxrwx--- 1 arta users 12288 2007-10-10 13:29 windows

```

Unfortunately, the second drive ("spare") is refusing to do as it's told! It still mounts as root with full permissions on everything, despite having the same options as the other drives in fstab:

```

root@arta-serv:/mnt# cat /etc/fstab
[snip]

/dev/sda1       /mnt/archive    ntfs-3g errors=remount-ro,fmask=0117,dmask=0007,uid=arta,gid=users      0       0
/dev/hdc1       /mnt/spare      ntfs-3g errors=remount-ro,fmask=0117,dmask=0007,uid=arta,gid=users      0       0
/dev/hda1       /mnt/windows    ntfs-3g errors=remount-ro,fmask=0117,dmask=0007,uid=arta,gid=users      0       0

```

Thanks in advance for any suggestions!

---

### Post by volksman on 2007-10-31
Just a suggestion but who owns the mount points before they are mounted?  IE what are the perms on spare before you run the mount command...compare that to archive before running mount...

---

### Post by drumstin on 2007-10-31
Can you chown/chmod on /dev/hdc1 ??

---

### Post by HarryM on 2007-10-31
Thanks for the quick replies!

I've tried chowning before the mount, it doesn't work: while the drive is mounted it's owned by root:root, and when unmounted it reverts back to the pre-mount permissions.

drumstin: I'm not sure what you mean! I've never heard of chowning the actual device. I tried this but it didn't make any difference:

```

root@arta-serv:/mnt# umount spare
root@arta-serv:/mnt# chown arta:users /dev/hdc1
root@arta-serv:/mnt# mount -a

```

---

### Post by HarryM on 2007-10-31
Hmm.

I just restarted for another problem and "spare" now shows up correctly. I thought Linux didn't do the "fixed by a reboot" thing!

Thanks for the suggestions, all working now.

---

