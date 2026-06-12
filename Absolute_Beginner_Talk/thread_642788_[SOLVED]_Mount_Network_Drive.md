---
title: "[SOLVED] Mount Network Drive"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by ghandi69_ on 2007-12-17
Ok guys, I have followed some of the threads here, and I have been able to run a command to mount my network drive.

However, I seem unable to to get the correct line in fstab to allow it to mount upon startup.

The command I use in the terminal is

>  sudo mount -t cifs -o username=adminz,password= //192.168.1.110/MyFiles /home/name/Server1


How would I get this to happen upon startup?

---

### Post by kpkeerthi on 2007-12-17
Assuming your mount command works, here is what you need to add to /etc/fstab

```

//192.168.1.110/MyFiles /home/name/Server1 cifs username=adminz,password= 

```

Save and Exit and type
```

sudo mount -a

```
to mount the filesystems configured in fstab. It should automount next time you reboot.

---

### Post by candtalan on 2007-12-17
I am very new to this subject. My network attached storage is formatted FAT32 and  I did not get success with cifs, only smbfs. I guessed that the box did not have a cifs server, although I know so little about this subject this may be a misunderstanding. The spec says it has smb server, ftp server and has a direct usb connection. I use it as a NAS.
I am just feeling my way with this at present.
My fstab line is:

#Mount of Network attached storage box
//192.168.1.42/store1 /home/user1/NAS-mnt smbfs uid=1000,umask=000,user,rw   0      0


hth

---

### Post by ghandi69_ on 2007-12-17
> **kpkeerthi said:**
> Assuming your mount command works, here is what you need to add to /etc/fstab

```

//192.168.1.110/MyFiles /home/name/Server1 cifs username=adminz,password= 

```

Save and Exit and type
```

sudo mount -a

```
to mount the filesystems configured in fstab. It should automount next time you reboot.

That.... was beautiful.

Thank You.

---

