---
title: "Permissions for a HD"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by guddr on 2007-06-25
I changed slave HD's and now have a locked HD that is owned as root.  I cant change permissions or use it.  How do I fix this situation?

---

### Post by daimaru on 2007-06-25
ok just guessing here but you might have wrong premissions on that hd. do this in terminal:
```
cd /media 
ls -la

```
if your hd is listed as having no rw then u dont have permissions you could change that by running
```
sudo chmod 776 /media/hda1
``` 

or what your hd is called .. otherwise if that does not work post your /etc/fstab file

---

### Post by guddr on 2007-06-25
Here is what I get from ls -la:  I no longer have HD30.

macd@macd-desktop:~$ cd /media
macd@macd-desktop:/media$ ls -la
total 32
drwxr-xr-x  8 root root 4096 2007-06-25 16:07 .
drwxr-xr-x 22 root root 4096 2007-06-23 19:39 ..
lrwxrwxrwx  1 root root    6 2007-06-16 07:32 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-06-16 07:32 cdrom0
drwxr-xr-x  2 root root 4096 2007-06-16 07:32 cdrom1
lrwxrwxrwx  1 root root    7 2007-06-16 07:32 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-06-16 07:32 floppy0
-rw-r--r--  1 root root    0 2007-06-25 16:07 .hal-mtab
--wxr-x---  1 root root    0 2007-04-15 07:56 .hal-mtab-lock
drwxr--r--  2 root root 4096 2007-06-20 10:31 HD30 
drwxrwxr-x  3 macd macd 4096 2007-06-24 15:33 HD40
drwxr-xr-x  2 root root 4096 2007-06-21 18:19 hdb1
macd@macd-desktop:/media$

---

### Post by rklauco on 2007-06-25
Question is where is the mountpoint.
Try opening a console and running a command
```

sudo chown -R youruser:yourgroup /the/mount/moint

```
This should change the owner of the folder and all it's subfolders for your user.
If you are not sure about your group, try in console the command
```

id

```
it will give you the default group id (gid) and you will find the default group name in brackets right behind. Usualy it is the same as username in default installation...

---

### Post by guddr on 2007-06-25
Here is what i got.  Im not sure what I should type in the terminal.  Thanks for ur help.

macd@macd-desktop:~$ id
uid=1000(macd) gid=1000(macd) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(macd)
macd@macd-desktop:~$

---

### Post by daimaru on 2007-06-25
is it he hdb1 that is not working ? if so do 
sudo chmod 777 hdb1

as far as i can see you should have read and execute permissions on hdb1 but not write permission. but this might be too high for me maybe some experts can help u out. just so they can help could you post ur /etc/fstab file too please.

just as a comparison heres my output of media
```
daimaru@daimaru:/media$ ls -la
total 30
drwxr-xr-x  8 root root 4096 2007-04-15 14:03 .
drwxr-xr-x 23 root root 4096 2007-06-25 17:40 ..
lrwxrwxrwx  1 root root    6 2007-06-25 18:13 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 2007-04-18 19:37 cdrom0
lrwxrwxrwx  1 root root    7 2007-06-25 18:13 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-06-25 18:13 floppy0
-r-Sr-----  1 root root    0 2007-04-15 14:03 .hal-mtab-lock
drwxrwxrwx  1 root root 4096 2007-06-24 18:36 hda1
drwxrwxrwx  1 root root 4096 2007-06-24 22:25 sda1
drwxrwxrwx  1 root root 4096 2007-06-24 18:36 sdb1
drwxrwxrwx  1 root root 4096 2007-06-24 18:36 sdc1
daimaru@daimaru:/media$ ls
cdrom  cdrom0  floppy  floppy0  hda1  sda1  sdb1  sdc1
daimaru@daimaru:/media$ 
```

as you can see all my hd's (hda, sda sdb sdc) have full permissions (chmod 777) so try that on your system. 
sry i cant be of more help :(:(

---

### Post by Inxsible on 2007-06-25
Type in 
 
```
sudo chown -R macd:macd /path/to/the/mount/point
```

---

### Post by guddr on 2007-06-25
Thanks for your suggestions.  Here is a copy of my etc/fstab:

<file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=5813bc4f-c17b-4955-911a-e3b2c894c62f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=259f0aa6-59ce-40fc-99ad-babebbb127d6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/HD40 ext3 defaults,errors=remount-ro 0 1
macd@macd-desktop:~$

---

### Post by Inxsible on 2007-06-25
> **guddr said:**
> Thanks for your suggestions. Here is a copy of my etc/fstab:
 
<file system> <mount point> <type> <options> <dump> <pass>
 
proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=5813bc4f-c17b-4955-911a-e3b2c894c62f / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=259f0aa6-59ce-40fc-99ad-babebbb127d6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[COLOR=red]/dev/hdb1 /media/HD40 ext3 defaults,errors=remount-ro 0 1[/COLOR]
[EMAIL="macd@macd-desktop:~$"]macd@macd-desktop:~$[/EMAIL]
 
Why do you have options like that of the root file system?
 
If hdb1 doesnt have a Linux OS install on it, it should look more like
 
```
/dev/hdb1 /media/HD40 ext3 defaults 0 2
```

---

### Post by guddr on 2007-06-25
I typed in sudo chown -R /media/HD40 but the HD still shows a lock.

---

### Post by Inxsible on 2007-06-25
From your earlier post:
 
HD40 is already owned by macd:macd
HD30, however, is owned by root:root

---

### Post by Inxsible on 2007-06-25
> **guddr said:**
> I typed in sudo chown -R /media/HD40 but the HD still shows a lock.
 
Thats coz you didnt enter your username and group
 
Do this:
 
```
sudo chown -R macd:macd /media/HD40
```

---

### Post by guddr on 2007-06-25
That was  a suggestion from someone else a while ago.  I am going to use HD40 as storage and it is formatted etc3. It has no data on it at all.

---

### Post by rklauco on 2007-06-25
> **guddr said:**
> I typed in sudo chown -R /media/HD40 but the HD still shows a lock.
Did it came up with some error message?
I believe the HD30 is no longer mounted, so we are talking about the HD40 drive.
And, the command should be
```
sudo chown -R macd:macd /media/HD40
```
This should work - I have mine one set like this.

---

### Post by Inxsible on 2007-06-25
> **guddr said:**
> That was a suggestion from someone else a while ago. I am going to use HD40 as storage and it is formatted etc3. It has no data on it at all.
 
 
I guess you mixed up two commands
 
chmod will NOT have your username and group.
chown WILL.
 
Is this an external drive that you are trying to mount? You should use pmount in that case !!!

---

### Post by guddr on 2007-06-25
This is what I get when I type that in:

macd@macd-desktop:~$ sudo chown -R macd:macd /media/HD40
macd@macd-desktop:~$ 

Nothing seems to change.  Should I be in another directory before typing those lines?

---

### Post by guddr on 2007-06-25
This is an internal drive im trying to use.

---

### Post by pingpongboss on 2007-06-25
> **guddr said:**
> This is what I get when I type that in:

macd@macd-desktop:~$ sudo chown -R macd:macd /media/HD40
macd@macd-desktop:~$ 

Nothing seems to change.  Should I be in another directory before typing those lines?

pretty sure chown doesn't give any output unless there's errors

---

