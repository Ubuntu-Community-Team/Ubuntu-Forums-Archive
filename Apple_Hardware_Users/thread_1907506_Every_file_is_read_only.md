---
title: "Every file is read only"
date: 2012-01-11
forum: Apple Hardware Users
---

### Post by jbills on 2012-01-11
I just installed the eclipse android development kit tool. now every file and folder on my system is read only. The installation of the eclipse plugin is the only thing I can think of that could be causing this. Does anyone know what has happened? I need some help.

**Update**: when I try to do anything I get the error "Read-only file system"

---

### Post by Lars Noodén on 2012-01-11
What is the output of [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html)?  You may have to boot into the rescue CD to do some maintenance.

---

### Post by jbills on 2012-01-11
I get 
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/josiah/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josiah)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.

```

---

### Post by jbills on 2012-01-11
How do you move a thread. It accidentally got into the Apple forum.

---

### Post by oldos2er on 2012-01-11
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1907513](http://ubuntuforums.org/showthread.php?t=1907513)

---

