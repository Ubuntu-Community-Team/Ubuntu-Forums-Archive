---
title: "can't share docs between xp and ubuntu"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by blairm on 2008-02-14
Hi,

Strugging along trying to dual boot xp and ubuntu with a shared fat32 partition.
Windows and ubuntu are working fine individually, but documents created in one o/s don't seem to be visible in the other.
Basically, have one ntfs partition of about 25gb for xp, another (ext3 from memory) of about the same size for ubuntu, about 1.5gb swap and the rest of the 160gb hard drive was left as the (hopefully) shared fat32 portion.
What do I need to do to share the documents between the operating systems???
Have been trying to get this set up for three days, and it's driving me to distraction!!!

Blair

---

### Post by spiderbatdad on 2008-02-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by blairm on 2008-02-14
thanks for the link... tried that, and although it gives me read-only access to documents created in windows I can't edit them.
In addition, when I try to save documents created in ubuntu to the shared partition I get an error telling me it doesn't exist,

Cheers,

Blair

---

### Post by spiderbatdad on 2008-02-15
you might post your /etc/fstab  for review.

---

### Post by spiderbatdad on 2008-02-15
my understanding of umask values is that permissions to the mount point are 777 minus the umask, so 0222 would be  555 or read, execute. So you may want umask=000.  There is also some information in  ```
man mount
``` regarding file specific permissions, where you actually set dmask and fmask.

I'll look for a post I recently saw where this was solved.

[http://ubuntuforums.org/showthread.php?t=685427&highlight=fmask](http://ubuntuforums.org/showthread.php?t=685427&highlight=fmask)

---

### Post by blairm on 2008-02-15
Hi,

Thanks for your help; please forgive any stupid questions I'm asking, have used Ubuntu for two years but never really delved into it until now.
The fstab stuff below, as requested...

Blair

 GNU nano 2.0.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=701e421b-bfd9-4298-980c-c0e2b5f12073 /               ext3    defaults,erro$
# /dev/sda1
UUID=F0D8368BD8365058 /media/sda1     ntfs    defaults,umask=0222, 0 0
# /dev/sda2
#UUID=47B5-6C14  /windows/sda2     vfat    defaults,utf8,umask=000, 0 0
# /dev/sda4
UUID=b99f8545-8d6c-4336-9e3b-6224118639d6 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by dstew on 2008-02-15
Did you notice that the fstab line for your /dev/sda2 partition is commented out? Remove the # from in front of the line, and do **sudo mount -a** and see if it works.

---

### Post by blairm on 2008-02-15
Thanks for your reply, Dstew; removed the comment, I must have put it in by accident.
Below is the amended fstab and the error message I get with sudo mount -a

Blair

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=701e421b-bfd9-4298-980c-c0e2b5f12073 /               ext3    defaults,erro$
# /dev/sda1
UUID=F0D8368BD8365058 /windows/sda1     ntfs    defaults,umask=0222, 0 0
# /dev/sda2
UUID=47B5-6C14  /windows/sda2     vfat    defaults,utf8,umask=000, 0 0
# /dev/sda4
UUID=b99f8545-8d6c-4336-9e3b-6224118639d6 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


robin@timaru-desktop:~$ sudo mount -a
fuse: failed to access mountpoint /windows/sda1: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 ()
mount: mount point /windows/sda2 does not exist
robin@timaru-desktop:~$

---

### Post by spiderbatdad on 2008-02-15
I notice you are logged in as a user other than owner. Are you sure you have permission to perform administrative tasks? Allow use of fuse filesystems  is one of the privileges listed under System>>Administration>>Users and Groups>>Your Name>>Properties>>User Privileges.

---

### Post by blairm on 2008-02-15
Hi Spiderbatdad,

Yes, I'm logged in as the owner - a computer I'm setting up for my parents, who want access to documents from xp and ubuntu.
Starting to get really puzzled here, and after reading a heap of guides on the subject starting to wonder where I've gone wrong! This has filled in the past three days pretty nicely!

Blair

---

### Post by spiderbatdad on 2008-02-15
try replacing umask in the fat partition line of fstab with: dmask=027,fmask=137
then mount manually using mount -t.

I'm sure I cannot help much. Sounds like you've done more reading and work on this subject than I. I do not dual boot. However, one last idea...there is a graphical program...it's fairly new...called disk manager. It is supposed to automate and make the whole process very user friendly. Here's the linky: [http://flomertens.free.fr/disk-manager/features.html](http://flomertens.free.fr/disk-manager/features.html)


If you install Disk Manager, it locates itself in System>>Administration.

---

### Post by dstew on 2008-02-15
The mount program seems to think the mount points do not exist. Are you sure they are there? Do **ls -l /windows** to see.

---

### Post by blairm on 2008-02-15
Hi again Dstew,

Here's the output from the command you suggested.


robin@timaru-desktop:~$ ls -l /windows
total 4
drwxrwxrwx 1 root root 4096 2008-02-16 13:11 sda1
robin@timaru-desktop:~$ ls -l /windows

---

### Post by dstew on 2008-02-15
There are two separate problems. The first is that the program **fuse** is attempting to mount your /dev/sda1 file system, and has come away unhappy. A fuse filesystem is, I think, remotely mountable. My guess is that fuse is trying to mount /dev/sda1, but does not have root permissions. Since the mount point is owned by root, it fails. You might need to reconfigure fuse.

The second is easier. The mount point /windows/sda2 does not exist. Once you create the mountpoint, try again. ```
sudo mkdir /windows/sda2
```

---

### Post by zerhacke on 2008-02-15
> **blairm said:**
> 
fuse: failed to access mountpoint /windows/sda1: No such file or directory

This tells me you have not created the /windows/sda1 directory on your computer yet.

---

### Post by blairm on 2008-02-15
Hi,

Thanks for the help from everyone, think we're making progress. Used the mkdir command and then tried sudo mount-a again, and got no error message, so I guess that's progress.
However, still can't access docs between operating systems.
For review, here's what I think are the relevant chunks of text:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58da58da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3210    25784293+   7  HPFS/NTFS
/dev/sda2            3211       15948   102317985    b  W95 FAT32
/dev/sda3           15949       19246    26491185   83  Linux
/dev/sda4           19247       19457     1694857+  82  Linux swap / Solaris



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda3 :
UUID=701e421b-bfd9-4298-980c-c0e2b5f12073       /       ext3    defaults,errors$
#Entry for /dev/sda2 :
UUID=47B5-6C14 /windows/sda2 vfat defaults,utf8,umask=000, 0 0
#UUID=47B5-6C14 /shared\040/sda2        vfat    defaults,utf8, umask=0222,     $
#Entry for /dev/sda1 :
UUID=F0D8368BD8365058   /windows/sda1   ntfs-3g defaults,locale=en_NZ.UTF-8    $
#Entry for /dev/sda4 :
UUID=b99f8545-8d6c-4336-9e3b-6224118639d6       none    swap    sw      0      $
/dev/hda        /media/cdrom0   udf,iso9660     user,noauto,exec        0      $

Any suggestions would be greatly appreciated!

Thanks,

Blair

---

### Post by dstew on 2008-02-15
> However, still can't access docs between operating systems.Do you mean you can't see the files in /dev/sda2 or /dev/sda1 from Ubuntu, or from Windows?

---

### Post by blairm on 2008-02-15
Hi,

Thanks for hanging in so long!
When I save a document in XP (have tried saving to my documents and shared documents) it's not visible in Ubuntu.
And when I create a document in Ubuntu, a search doesn't find it anywhere in XP.

Blair

---

### Post by spiderbatdad on 2008-02-15
possibly still a permissions problem in fstab. Also I have seen problems mounting when windows is not cleanly shut down. I don't think you can hibernate windows and then mount the drive in Ubuntu.

---

### Post by dstew on 2008-02-15
> When I save a document in XP (have tried saving to my documents and shared documents) it's not visible in UbuntuWhat do you mean by this? Where are you looking for the documents? They don't just appear on the desktop! You have to look into the /windows/sda1 or /windows/sda2 folders, depending on which partition you saved it in. In fact, post the output of the commands```
ls -l /windows/sda1
ls -l /windows/sda2
```Let's see what's in there.

---

### Post by blairm on 2008-02-15
Hi,

Here's the output of the commands, as requested.
When searching for the documents in ubuntu, went through pretty much every place in the places menu looking for them; the file names didn't come up in a search either.
Really appreciate everyone taking the time to help me here.

Blair
  
robin@timaru-desktop:~$ ls -l /windows/sda1
total 1376597
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        223 2008-02-16 12:15 boot.ini
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-02-16 08:29 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 IO.SYS
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2006-03-01 01:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2006-03-01 01:00 ntldr
-rwxrwxrwx 1 root root 1409286144 2008-02-17 11:23 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-02-16 13:10 Program Files
drwxrwxrwx 1 root root       4096 2008-02-16 08:27 System Volume Information
drwxrwxrwx 1 root root      28672 2008-02-16 12:27 WINDOWS
robin@timaru-desktop:~$ ls -l /windows/sda2
total 16
drwxrwxrwx 3 root root 16384 2008-02-15 11:29 System Volume Information
robin@timaru-desktop:~$ ls -l /windows/sda2

---

### Post by dstew on 2008-02-15
Well, that is your Windows C: drive directory listing. You have to navigate through it just like you would on Windows to find your files. To look into the Documents and Settings folder, just change to that directory:```
cd 'Documents and Settings'
```You need single quotes because the directory name has spaces in it. Then, do```
ls -l
```and you will see the files in that directory, and so on. You should also be able to do this with the graphical file manager on the desktop (Places menu).

---

### Post by blairm on 2008-02-15
Hi,

Tried what you suggested and found there is no documents and settings file or directory (see below). Can't see them in the place graphic interface either - there is a documents file, but it's empty.

robin@timaru-desktop:~$ ls -l /windows/sda1
total 1376597
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        223 2008-02-16 12:15 boot.ini
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-02-16 08:29 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 IO.SYS
-rwxrwxrwx 1 root root          0 2008-02-16 08:24 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2006-03-01 01:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2006-03-01 01:00 ntldr
-rwxrwxrwx 1 root root 1409286144 2008-02-17 11:23 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-02-16 13:10 Program Files
drwxrwxrwx 1 root root       4096 2008-02-16 08:27 System Volume Information
drwxrwxrwx 1 root root      28672 2008-02-16 12:27 WINDOWS
robin@timaru-desktop:~$ cd 'Documents and Settings'
bash: cd: Documents and Settings: No such file or directory
robin@timaru-desktop:~$ 

Cheers,

Blair

---

### Post by dstew on 2008-02-16
> there is no documents and settings file or directoryHere it is:```
drwxrwxrwx 1 root root 4096 2008-02-16 08:29 Documents and Settings
```

---

### Post by scradock on 2008-02-16
remember, unlike WindOws, Linux is case-sensitive!   Documents is a different name from documents

---

### Post by shadowmaster79 on 2008-02-16
just do
sudo mkdir -p /windows/sda1

---

### Post by shadowmaster79 on 2008-02-16
sorry have not read to end :popcorn:

---

### Post by blairm on 2008-02-16
Thanks to everyone for their help and patience, but I admit defeat.

Have gone back to a straight dual-boot without a shared partition, which I was able to set up with no  problems.

Think I'll have to install ubuntu on a spare machine and use it to learn more about what goes on under the hood - has become apparent over the past few days this that I need to know more, and although it has been frustrating, it's been interesting as well.

Cheers,

Blair :)

---

