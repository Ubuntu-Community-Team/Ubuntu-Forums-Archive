---
title: "why the &quot;owner owner-group&quot; is &quot;root plugdev&quot;"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by greeenlife on 2007-08-16
when  i use firefox  to login my ftp server and wanna change directory to "movie&music",there is a message "550 failed to change directory"

/home/ftp/movie&music is a symbolic to /media/sda6 as following:
> 
root@djtu2123:/home/ftp# cat /etc/fstab | grep sda6
# /dev/sda6
UUID=A8B9-E18F  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
root@djtu2123:/home/ftp# ln -s /media/sda6/ /home/ftp/movie\&music
root@djtu2123:/home/ftp# ls -l
total 4
lrwxrwxrwx 1 root root   12 2007-08-16 13:25 movie&music -> /media/sda6/
drwxr-xr-x 4 root root 4096 2007-08-15 13:13 pub
root@djtu2123:/home/ftp# ls -l /media/ | grep sda6
drwxr-x--- 7 root plugdev 16384 1970-01-01 08:00 sda6

root@djtu2123:/home/ftp# /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                                [ OK ] 
 * Starting FTP server: vsftpd                                                                [ OK ] 

root@djtu2123:/home/ftp# ftp localhost
Connected to localhost.
220 Welcome to blah FTP service.
Name (localhost:djtu): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd movie&music
550 Failed to change directory.
ftp> 


how should i do?

thanks a lot!

---

### Post by kevstar31 on 2007-08-16
Can you post /etc/fstab?

---

### Post by thuleni on 2007-12-15
My permissions have changed on my internal Windows drive to root plugdev as well.  WHY?

---

### Post by schorsch on 2007-12-15
Vfat partitions do not support permissions as linux or ntfs partitions. You have to set the right permissions when you mount the partition so an entry in /etc/fstab will do the trick.

```
/dev/hda1 /media/hda1 vfat rw,nosuid,nodev,utf8,umask=077,gid=1000,uid=1000, 0 1
```

Replace the values for gid and uid with the values for your user and group:
```
grep username /etc/passwd
```

Umount the drive and remount it:
```
sudo umount /dev/hda1
sudo mount /dev/hda1
```

... and your user should have write permissions. I used /dev/hda1 as an example so please change it as required.

---

### Post by thuleni on 2007-12-15
Cheers Schorsch - worked a treat.

---

### Post by ubuntu_jazzbach on 2008-05-05
It worked for me as well !
 
THANKS !!!!

---

### Post by FBurnaby on 2008-05-10
Thanks! This helped me, too!

---

