---
title: "cd won't work under sudo"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-03-03
I need to mount a hard drive from the Ubuntu 6.10 live cd. I can mount the hard drive without any problems, but I can't access the drive. The terminal says that I don't have enough access privelages, so I ran the command as the root user with "sudo." 

But, when I run the command using sudo, the terminal outputs the following:
sudo: cd: command not found

How can I access this volume?

---

### Post by cantormath on 2007-03-03
> **Shack_ said:**
> I need to mount a hard drive from the Ubuntu 6.10 live cd. I can mount the hard drive without any problems, but I can't access the drive. The terminal says that I don't have enough access privelages, so I ran the command as the root user with "sudo." 

But, when I run the command using sudo, the terminal outputs the following:
sudo: cd: command not found

How can I access this volume?

if you want to cd as sudo, 
sudo -i
the you are root
cd /folder/

---

### Post by taurus on 2007-03-03
What's the output of this command from a terminal?

```
df -h
```

---

### Post by teaker1s on 2007-03-03
live cd for me was buggy copying files, knoppix may suit you better

---

### Post by Shack_ on 2007-03-03
The output:

Filesystem          Size          Used          Avail          Use%          Mounted on
unionfs               1.7G         649M          997M         40               /
varrun                1013M      76K            1013M        1                /var/run
varlock               1013M      0                1013M        0                /var/lock
procbususb         10M          160K          9.9M           2                /proc/bus/usb
udev                   10M          160K          9.9M          2                /dev
devshm              1013M       0               1013M        0                /dev/shm
lrm                     1013M      7.6M           1006M       1                 /lib/modules/2.6.17-10-generic/volotile
tmpfs                 1013M       16K            1013M        1                /tmp
/dev/sda1           47M          6.9M           41M           15               /media/windows
/dev/sda2           10G          4.3G           5.8G          43               /media/primary
/dev/sda3           223G        86G            138G         39               /media/test

Sorry if the "table" isn't aligned correctly, I had to copy this over to a Windows PC because I have dial-up.

What did you want me to do this for?

---

### Post by taurus on 2007-03-03
Which partition do you want to have access to (read-only--ntfs) without using sudo?  We are going to remount it with the right permission so you can read from it.

---

### Post by Shack_ on 2007-03-03
Actually, I just need to know the general command, because I'm trying to figure out which volume is which. I don't care if you use /media/windows, /media/primary, or /media/test, because I'm going to try others eventually.

And seriously, what does df -h do? I really would like to know.

---

### Post by taurus on 2007-03-03
```
sudo umount /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o nls=utf8,umask=0222
cd /media/windows
ls -la
```

df shows filesystem disk space usage and mount point with -h as human-readable option.

```
man df
```

---

### Post by omrsafetyo on 2007-03-03
After mounting the drive, shouldn't he just be able to chown the mountpoint??

sudo chown /home/windows
sudo chmod ug+rw /home/windows

run an  ls -l from the media directory, and that will tell you the permissions on that mountpoint.  If you are not the owner, that would be why you can't access it.

Oh.. yeah... unless he mounted it with the wrong filesystem type..  e.g. ext3 instead of ntfs

---

### Post by taurus on 2007-03-03
Chown and chmod will not work on ntfs or fat32 filesystems.

---

### Post by omrsafetyo on 2007-03-03
> **taurus said:**
> Chown and chmod will not work on ntfs or fat32 filesystems.

Thats right.. I forgot the permissions worked differently.  I'll just watch, and let the experts find the solution.  :)

---

