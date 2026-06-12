---
title: "confused about partition not showing up"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by octathlon on 2007-06-16
Hi,
I am wondering why a partition that is mounted and shows up fine in Konqueror or Nautilus, does not show up in the output of df when I am checking free space.  

Here are the disk partitions,  hdb7 is the Ubuntu partition:
```
gjd@IBM-DT1:~$ sudo fdisk -l /dev/hdb
Password:

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14       21095   169341165    5  Extended
/dev/hdb5              14         209     1574338+  82  Linux swap / Solaris
/dev/hdb6             210        2819    20964793+  83  Linux
/dev/hdb7            2820        5430    20972826   83  Linux
/dev/hdb8            5431       13263    62918541   83  Linux
/dev/hdb9           13264       21095    62910508+   c  W95 FAT32 (LBA)

```


Here's my fstab, (I don't mount hdb6)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0                  1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb8       /mnt/data       ext3    defaults,uid=1000,gid=100       0      0
/dev/hdb9       /mnt/share      vfat    iocharset=utf8,umask=000        0      0

```

Here is the result of **df -h**
```

gjd@IBM-DT1:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hdb7              20G   12G  6.8G  64% /
varrun                252M   76K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-28-386/volatile
/dev/hda1              38G  2.6G   35G   7% /media/hda1
/dev/hdb9              60G  661M   60G   2% /mnt/share

```

See how **/dev/hdb8 doesn't show up**, yet hdb7 abd hdb9 do show up.  Can anyone tell me why that is, and how to fix it?


By the way, /hdb8 is mounted as "data" and shows up fine in commands like ls:
 ```

gjd@IBM-DT1:/mnt$ ls -l
total 44
drwxrwxrwx 10 gjd  root  4096 2007-06-12 20:07 data
drwxr-xr-x  2 root root  4096 2006-07-17 18:31 hdb1
drwxr-xr-x  2 root root  4096 2006-07-17 18:27 hdb6
drwxrwxrwx  9 root root 32768 1969-12-31 19:00 share
                                       
```

Thanks,

---

### Post by mahiyar on 2007-06-16
ls -l just shows the directories created for mounting. If you look in to that particular directory i.e /mnt/share I bet it will be empty. I guess that this particular partition is having problem mounting on boot, since it is not mounted it does not show in the df -h command. Try mounting it manually and look for the errors.

---

### Post by octathlon on 2007-06-16
Thanks for the reply.  That directory is actually mounted and I can go into it, list and open the files under it from either the command line or from Konqueror.  That's what is so confusing.

For example, here I opened a file on that partition (I have not manually mounted anything):
```

gjd@IBM-DT1:/mnt/data/downloads$ cat zenwalk-live-4.4.1.iso.md5
4dc7a5317359d7c4487d373bcae90add  zenwalk-live-4.4.1.iso
gjd@IBM-DT1:/mnt/data/downloads$ 
```

---

### Post by mahiyar on 2007-06-16
try sudo df -h

---

### Post by octathlon on 2007-06-17
Funny you mention it, I did that right after my last post when I suddenly noticed that it was the only directory not owned by root.  :)  Unfortunately, the result was the same:

```
gjd@IBM-DT1:~$ sudo df -h
Password:
Filesystem            Size Used Avail Use% Mounted on
/dev/hdb7              20G   12G  6.8G  64% /
varrun                252M   76K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-28-386/volatile
/dev/hda1              38G  2.6G   35G   7% /media/hda1
/dev/hdb9              60G  661M   60G   2% /mnt/share
```


I suppose it could have something to do with the way I have it set up in fstab, but I don't see what the problem would be.

---

### Post by mahiyar on 2007-06-17
The problem seems to be that in fstab you have used uid and gid, try removing these keep it like this.

/dev/hdb8       /mnt/data       ext3    defaults     0      0

Save fstab. No need to reboot, use this command >>sudo mount -a.
Then see df -h again.
See this link for better understanding of fstab [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by octathlon on 2007-06-17
I tried your changes and now I can see it listed on df.  However, that creates the problem that I can no longer see any of the files or subdirectories under /mnt/data at all, either as myself or with sudo, because I don't have permission anymore.  But we are on the right track knowing it's related to the fstab setup, I will need to read up on this some more.

---

### Post by mahiyar on 2007-06-17
This explains -- the data directory that you created had this permissions thing. What you can do is create another directory in mnt (I usually use /media to create mounted directories) change fstab accordingly and them mount the same.

---

### Post by octathlon on 2007-06-17
> This explains -- the data directory that you created had this permissions thing. What you can do is create another directory in mnt (I usually use /media to create mounted directories) change fstab accordingly and them mount the same.


I'm not sure I understand what you mean.  Do you mean that root must be the owner of /mnt/data ?  I wanted my login to be the owner and not allow others not in my group to access the directory, for security reasons.  Since I was running the df command as the directory's owner, I should be able to see that directory, just as I see it with any other command (unless there are others besides df that I don't know of that would have this problem).

---

### Post by mahiyar on 2007-06-17
Did you see the link I had given? In it the directory, fstab were created the normal way and later on the permissions were amended for the directory.

---

### Post by octathlon on 2007-06-17
Yes, I tried doing it like in the link.  All I have managed to do now is make it so that I can no longer access the partition/directory, either as myself or as sudo.  It is mounted, and I am the owner, with 755 permissions, but I can't even view it.

It seems that every time I touch anything to do even the simplest thing, I get the system more and more screwed up.  I think I have to admit, Linux is too hard for me.  I follow instructions to the letter, and it never comes out like it's supposed to.   Now, even when I tried to restore my fstab by replacing it with the backup I made, it no longer works [EDIT: I had to restart the system after replacing fstab with the backup. I now have everything back the way it was before].  

I used to work on Unix systems years ago, but I understood it and things worked for me then. Now with Linux, things don't make sense.  I see no reason why the df command doesn't display /mnt/data.  I own the directory.  The way the article had permissions set for the directory is how I had them set, yet if I set fstab the way they have it (defaults, no uid), then I can't access the directory.  Why does it work for them and not for me?

---

### Post by mahiyar on 2007-06-19
It should not be a problem. Lets go step by step. First put aside your need to create a folder/partition for you only. Create a normal folder in /media. Create a normal line in fstab to mount the partiton in question and see whether you can access it. 

BTW : I hope you are logging in with the same login that you had originally created when installing Ubuntu.

---

### Post by octathlon on 2007-06-19
I started over with a new directory, and it worked this time.  Thanks a lot for your help!

---

### Post by mahiyar on 2007-06-19
Another wonderful learning site is community docs this page explains fstab, mounting etc in great detail [http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

