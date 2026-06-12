---
title: "[SOLVED] Why doesn't NTSF mount automatically on my Ubuntu 7.10?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by denizkural on 2008-04-03
Hi,

I have a dual-boot IBM T60p, with windows xp and Ubuntu 7.10 ... but I used to have an older version of ubuntu when I first did the dualboot, and had access to "IBM_PRELOAD" on my desktop, so I could access my windows files.

But I noticed today that for some reason, I can't find IBM_PRELOAD, and it is not mounted. The problem is, although I could mount it, I don't want to do something wrong -- the guide at

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=MountNtfsOnBoot)

says that 7.10 automatically mounts the NTSF partitions... so why doesn't mine?

Any ideas why IBM_PRELOAD disappeared on me?  The only thing I can think of is that I created a new user on my computer, but I am not logged in with that new user so I don't see how that is relevant.

Help is much appreciated,
Deniz

---

### Post by nathansoz on 2008-04-03
Edit your /etc/fstab file

at the end of the file put

/dev/(device name)   /media/(name of device)      ntfs      default    0      2

all with a tab in between them

NOTE: you may have to create the mount point folder (/media/(name of device))

---

### Post by ghost_ryder35 on 2008-04-03
> **nathansoz said:**
> Edit your /etc/fstab file

at the end of the file put

/dev/(device name)   /media/(name of device)      ntfs      default    0      2

all with a tab in between them

NOTE: you may have to create the mount point folder (/media/(name of device))
:guitar:

---

### Post by c-ron on 2008-04-03
> **nathansoz said:**
> Edit your /etc/fstab file

```
sudo gedit /etc/fstab
```

> at the end of the file put

/dev/(device name)   /media/(name of device)      ntfs      default    0      2

all with a tab in between them



You can see your find the device name for the NTFS partition by running from the terminal:
```
sudo fdisk -l
```


> NOTE: you may have to create the mount point folder (/media/(name of device))

```
sudo mkdir /media/(name of device)
```

---

### Post by denizkural on 2008-04-03
Here is my fstab file:

Are you sure I should add yet another line? 

(thanks for the replies btw)


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  defaults                            0  0  
# /dev/sda2
UUID=d2548a75-d799-49f0-92b0-25ec7e14d968  /               ext3  defaults,errors=remount-ro          0  1  
# /dev/sda1
UUID=A0BC89E4BC89B576                      /media/windows  ntfs  defaults,nls=utf8,umask=007,gid=46  0  1  
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0/dev/sda2                                  /media/sda2     ext3  defaults                            0  0  
/dev/sda1                                  /media/sda1     ntfs  defaults                            0  0  


Thanks,
Deniz

---

### Post by joshrobinson on 2008-04-04
fstab is a filesystem configuration file
it tells linux/ubuntu what drives to mount automatically at boot, where they are located, what filesystem they are, where to mount them, and what permissions to mount them with

but im not sure why it dissapeared

---

### Post by denizkural on 2008-04-04
So ok, problem solved:

It seems that, when I turned off my computer, windows did not close 'cleanly'.

I rebooted my computer after I got a bluescreen, and just used linux after that...

So even if I shut down my computer and turn it on again, if I use linux, I couldn't mount the NTSF device. 

But when I booted up in windows, shut down properly, and restart in linux, voila, my IBM_PRELOAD came back. Strange huh? Ubuntu is smart.

Deniz

p.s. how do I describe this thread as "solved"?

---

### Post by joshrobinson on 2008-04-04
above your first post on the right there is a thread tools menu, click that and hit mark as solved

---

