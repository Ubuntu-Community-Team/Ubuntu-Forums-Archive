---
title: "Can't open Harddisk, Ubuntu 6.10"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by Alexanderfoto on 2006-11-17
Hello. Well, I'm here's a new ubuntu user for you! 
After I bought my MacBook I realized how sick and tired I was of Windows. So I'm a fully converted Mac OSX and Linux man now.

I first installed Suse 10.1. But I find the whole thing a bit...unstable? And the fact that I had to hack the whole thing before I could use it right was quite time consuming and a bit lame. Worked though. I managed to f*** up the system when I tried to install XGL :D So I decided instead of wasting time trying to fix it I'd just try Ubuntu as well. 

I do love the simplicity and it's fun to learn! 
Well, enough intro, you're probably bored. I'll proceed with my newbish question, don't think I didn't Google it!

In Windows I had two harddisks; C: and D: .. I formatted the C disk and installed Ubuntu. But my D disk (if I'm allowed to still call it that..) won't open! 

Ubuntus kind of detected it in dev => disk => by label (disk name:STORAGE). But in properties it states it's 0 bytes and if I click I get the following error:

Cannot open /dev/disk/by-label/STORAGE: No application is known for this kind of file. 

Please say I don't have to format this HD. 
Thank you,
Alex

---

### Post by taurus on 2006-11-17
You just need to mount it first before you can use it.  Here is a guide for you to look through.  

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Bachstelze on 2006-11-17
Hi and welcome to Ubuntu :)

What is in /dev is a file (called a "block device") which, to put it simply, represents the partition itself (and not the files stored on it).

To access the files, you need to *mount* the device, and to tell you how, we need a bit more info. Please paste the output of :

```
sudo fdisk -l
```

(Note that it's a lowercase L, not a capital i)

---

### Post by Alexanderfoto on 2006-11-17
Wow, quick replies. Awesome forum!
Thanks Taurus, though I got so far as step 7 and never found anything like  ```
" # /dev/hda1
UUID=FC98E2C598E27E10 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```



HymnToLife, output :)
```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3497    28089621   83  Linux
/dev/hda2            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    7  HPFS/NTFS
```

---

### Post by Bachstelze on 2006-11-17
All right, try this :

```

sudo mkdir /windows
sudo mount -t ntfs /dev/hdb1 /windos
```

If it's what you want, I'll tell you how to set it to mount automagically at boot time.

---

### Post by taurus on 2006-11-17
Edit your /etc/fstab and add this line to the end of it.

```

/dev/hdb1   /media/windows   ntfs   nls=utf8,umask=0222  0  0

```
Then, create a mount point and mount it.

```

sudo mkdir /media/windows
sudo mount -a
df -h

```

---

### Post by Alexanderfoto on 2006-11-17
Hymn: Done, but I'm not sure what I just did? Where can I find my mountable HD?

Taurus. I'm trying to edit in Terminal and get following:

Warning: unknown mime-type for "fstab" -- using "application/*"
Error: no write permission for file "fstab"

I'm not sure if there's a su mode in Ubuntu?

---

### Post by Bachstelze on 2006-11-17
If you dod what I tell you, you can access the files stored on your partition using whichever file manager you want, they're in /windows.

To edit the fstab file, run

```
sudo nano /etc/fstab
```

---

### Post by Alexanderfoto on 2006-11-17
Hmm..

The folder contents could not be displayed.
You do not have the permission necessary to view the contents of "windows".

---

### Post by taurus on 2006-11-17
> **Alexanderfoto said:**
>  
Taurus. I'm trying to edit in Terminal and get following:

Warning: unknown mime-type for "fstab" -- using "application/*"
Error: no write permission for file "fstab"


(Applications -> Accessories -> Terminal)

```
gksudo gedit /etc/fstab
```

---

### Post by Bachstelze on 2006-11-17
My mistake, you need to add a few parameters to the mount command to have permission to access it. Do what taurus told you and you should be fine.

---

### Post by Alexanderfoto on 2006-11-17
Alright, fstab edited. But there's no content in media/windows.

---

### Post by Bachstelze on 2006-11-17
You need to unmount the partitoin first to be able to mount it on the new mountpoint, do

```

sudo umount /dev/hdb1
sudo mount -a
```

---

### Post by taurus on 2006-11-17
> **Alexanderfoto said:**
> Alright, fstab edited. But there's no content in media/windows.
Okay, show me the output of these two commands from a terminal then.

```
cat /etc/fstab
df -h
```

p.s.  If you used my instruction, then it would have been /media/windows, not media/windows...

---

### Post by TheWizzard on 2006-11-17
> **HymnToLife said:**
> 
```
sudo nano /etc/fstab
```

if you use
```
sudo nano -B /etc/fstab
```[/QUOTE]
you backup the original file. can be handy if you mess stuff up ;)

---

### Post by Alexanderfoto on 2006-11-17
```
alex@Oblivious:/etc$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=aa3e88db-71b5-48e7-8b72-4e0948109758 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d37ae681-c9d8-4a90-85ed-5ce7e8094aea none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1   /media/windows   ntfs   nls=utf8,umask=0222  0  0

```


```

alex@Oblivious:/etc$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              27G  1.9G   24G   8% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  164K  9.9M   2% /proc/bus/usb
udev                   10M  164K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
tmpfs                1014M   18M  997M   2% /lib/modules/2.6.17-10-generic/volatile
/dev/hdb1             150G  143G  6.8G  96% /media/windows

```

---

### Post by Bachstelze on 2006-11-17
That's all right, now you should be able to access your stuff in /media/windows.

---

### Post by Alexanderfoto on 2006-11-17
Eureca!
Found my Harddisk. Thanks for your patience!

Edit: I'm not allowed to edit any content though?

---

### Post by juantovarm on 2006-11-17
can you edit the content inside your hard disk? see if you have the permission for it.

type: cd /media
      ls -l

post the results

Juan

---

### Post by taurus on 2006-11-17
> **Alexanderfoto said:**
> 
Edit: I'm not allowed to edit any content though?
It is NTFS filesystem and you only mount it as read only.  If you want to write to NTFS, you need to install ntfs-3g!

---

### Post by Alexanderfoto on 2006-11-17
alex@Oblivious:/media$ ls -l
total 48
lrwxrwxrwx 1 root root     6 2006-11-17 16:43 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2006-11-17 16:43 cdrom0
lrwxrwxrwx 1 root root     7 2006-11-17 16:43 floppy -> floppy0
drwxr-xr-x 2 root root  4096 2006-11-17 16:43 floppy0
drwx------ 9 alex alex 32768 1970-01-01 01:00 MAXTOR
dr-xr-xr-x 1 root root  8192 2006-11-15 17:36 windows



Downloaded ntfs 3g and installed. I guess I'll have to change the permissions. This is probably a Terminal thing considering I have to be root?

---

### Post by taurus on 2006-11-17
Actually, you need to change it in /etc/fstab.  Replace "ntfs" with "ntfs-3g" for /dev/hdb1.  Here is a guide if you want to read it.

[http://everythingelse.wordpress.com/2006/07/19/89/](http://everythingelse.wordpress.com/2006/07/19/89/)

p.s.  Don't forget to reboot after making the change in /etc/fstab...

---

### Post by brander on 2006-11-18
Hi, sorry to butt in, but I read the whole post because I had the same problem and got as far as mounting the drive. But my second drive was created as a logical drive in an extended partition by gparted and formatted as ext3.

I have got it mounted and can read/write from terminal in SU mode, but can only read files on the drive, not write them as a normal user.

I tried mounting it in my /home/user folder, but all my other files there seemed to disappear then until reboot. It only seemed to be happy in /mnt.

Is there some script I can use in terminal mode to change the permissions on the drive?  Thanks.

---

### Post by taurus on 2006-11-18
> **brander said:**
> Hi, sorry to butt in, but I read the whole post because I had the same problem and got as far as mounting the drive. But my second drive was created as a logical drive in an extended partition by gparted and formatted as ext3.

I have got it mounted and can read/write from terminal in SU mode, but can only read files on the drive, not write them as a normal user.

I tried mounting it in my /home/user folder, but all my other files there seemed to disappear then until reboot. It only seemed to be happy in /mnt.

Is there some script I can use in terminal mode to change the permissions on the drive?  Thanks.


If it is an ext3, then you can use the chmod command to change the permissions...  Open a terminal and type

```
sudo chmod -R 777 /mnt/<your mount point>
```

---

### Post by brander on 2006-11-18
Hi, thanks for that, I tried mounting the partition as sudo instead of su and that worked the same. However, in your instruction above, I do not know what to put in the <mount point> part.
I mounted the drive with
sudo mount /dev/hda5 /mnt

which works and I can read the files. So what should I enter for <mount point> in
sudo chmod -R 777 /mnt/<mount point>

---

### Post by brander on 2006-11-18
It`s OK I worked out that the <mount point> is whatever foldername I want to change permissions on. Working well now.

Thanks for the help.

---

### Post by taurus on 2006-11-18
> **brander said:**
> It`s OK I worked out that the <mount point> is whatever foldername I want to change permissions on. Working well now.

Thanks for the help.
By the way, I don't recommend you mount stuff to /mnt although it doesn't really matter.  Instead, create a mount point in /mnt like /mnt/backup and mount your ext2 to that, /mnt/backup...

---

### Post by brander on 2006-11-18
OK, will do that next time. Thanks.

---

### Post by Alexanderfoto on 2006-11-19
> **taurus said:**
> Actually, you need to change it in /etc/fstab.  Replace "ntfs" with "ntfs-3g" for /dev/hdb1.  Here is a guide if you want to read it.

[http://everythingelse.wordpress.com/2006/07/19/89/](http://everythingelse.wordpress.com/2006/07/19/89/)

p.s.  Don't forget to reboot after making the change in /etc/fstab...


I noticed this one...
```

#ntfs-3g & fuse-2.5 repo
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) **dapper** main
deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/)** dapper** main
```

Will it still work on my edgy?

---

### Post by Alexanderfoto on 2006-11-22
I understand 3g can be unstable. And something about AMD64 not supported? Didn't get that part. Anywho, I've been thinking about formatting my second and third harddisk and just take a backup and copy over after the format. How do I do this in Ubuntu?

---

### Post by taurus on 2006-11-22
> **Alexanderfoto said:**
> I understand 3g can be unstable. And something about AMD64 not supported? Didn't get that part. Anywho, I've been thinking about formatting my second and third harddisk and just take a backup and copy over after the format. How do I do this in Ubuntu?
You need to unmount the partitions that you want to format and use gparted to format them to vfat/fat32.  Then, mount them again by editing /etc/fstab...

---

