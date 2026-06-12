---
title: "&quot;Special&quot; mounting - can't figure it out myself"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Lycaon on 2006-06-22
Well hello people who are willing to help me,

Revisited:P

I installed ubuntu dapper drake server edittion on my server. That went well. A main daemon i am using in the server is glftpd. A pretty nice and good working ftp daemon. While installing dapper drake asks me for the partitioning table. I got 2 s-ata maxtor hdd's (sda and sdb). Here is the layout i chose to create:
> 
  SCSI1 (0,0,0) (sda) - 163.9 GB ATA Maxtor 6Y160M0
    #1 primary      2.0 GB    F  swap     swap
    #2 primary    20.0 GB  BF  ext3      /
    #3 primary  141.9 GB    F  ext3      /disc1
  SCSI2 (0,0,0) (sdb) - 160.0 GB ATA Maxtor 6Y160M0
    #1 primary  160.0 GB    F  ext3      /disc2


and the fstab after the install looks like this

> 
# <file system> <mount point>    <type>  <options>         <dump>  <pass>
proc                    /proc                    proc      defaults                  0            0
/dev/sda2           /                          ext3      defaults,errors=remount-ro 0 0
/dev/sda3           /disc1                  ext3      defaults                   0            2
/dev/sdb1           /disc2                  ext3      defaults                   0            2
/dev/sda1           none                   swap     sw                           0            0


So i continued installing some libs etc. After that i could install glftpd. Glftpd mkdirs this layout for the server dir's.
 /glftpd/site/
This dir is on /dev/sda2. When a user logs into the ftp server they will end up by default in the root directory of the server. That is /glftpd/site/.

While partioning earlier i created to big partions for my data. sda3 on hdd1 and sdb1 on hdd2 -> /disc1 & /disc2.
The thing i actually want is this:
[example]
  * i create directory called 'upload' on disc2: /disc2/upload
  * now i would like to have, when a user logs in he/she can see the dir upload in the ftp. If the user enters the directory it will be not in /glftpd/site/upload, but actually working in /disc2/upload.
  * Why? now i can have directories that dont have anything to do with the ftp on disc2 also. So I can specify what dirs ar shown in glftpd.
[/example]

This is what i have already tried:

> 
* Making a symlink from /disc2/upload to /glftpd/site/. This works i can see a shortcut when i loging called'upload'. However when i try to enter this dir it says: [2] CWD upload [2] 550 upload: No such file or directory.
   I can't enter it...and i just dont know why.  Everyone has all rights on that dir/disc
* Mounting in fstab, well after reading i figuered  out i cannot mount directories in fstab only filesystems. (thnx  mlind)
* i tried to bind a directory to another with: mount --bind /disc2/upload/ /glftpd/site/upload/
   and yes this fails too:( It seems to be uploading on the /glftpd/upload map instead of  /disc2/...


I hope this makes it some easier to read. Please give it another shot

---

### Post by mlind on 2006-06-22
It's hard to read your post with that layout. Could you summarise your problem a bit?

You can mount a partition, but not a certain directory from the partition
(as far as I've understood mounting process..). Mount is just for filesystems.

What you should probably do is to mount necessary filesystem on /media, /mnt
or where ever you want and then just create a symlink to devc++ folder on that
partition

[example]
partition /dev/hda is a ext3 type partition that contains folder named bar which
contens you want as /foo/bar. foo is a existing directory.

mount /dev/hda as /mnt/share. then create a symlink called bar on directory /foo
which points to /mnt/share/bar

```

sudo mkdir -p /mnt/share
sudo mount -t ext3 /dev/hda /mnt/share
sudo ln -sf /mnt/share/bar /foo/bar

```

create uid and gid rules (and umask too) on /etc/fstab for /dev/hda
so you can define what user and group gets ownership of the mount and what
their privileges are.

---

### Post by Lycaon on 2006-06-23
Thanx mlind, but the symlink doesnt work. I cannont navigate to the directory in the ftpd.

I noticed another weird thing, when i do : df -h. in a terminal i do not get /dev/sdb1 listed...is this normal?

---

### Post by Lycaon on 2006-06-23
I noticed some other things to:
when typing mount in the terminal it doesnt display /dev/sdb1
when i try to mount it normally it just say's:
/dev/sb1 already mounted or /disc2 busy

:confused:

---

### Post by catlett on 2006-06-23
[http://www.ubuntuforums.org/forumdisplay.php?f=45](http://www.ubuntuforums.org/forumdisplay.php?f=45) Post in that section. It is Ubuntu's "server talk" section. You will have a better chance with server questions there. Everyone is willing to help here but most won't have server installs/ Good luck.

---

### Post by Lycaon on 2006-06-23
allright will try that too:)
but i thought the mounting part is kinda for beginning users..

---

### Post by mlind on 2006-06-28
I was wrong about the "mount is just for filesystems" part.
You can mount directories too using **-bind** argument


I have a folder filled with music on my ntfs share, which is mounted as /media/D.
I'll mount one if its folders as /mnt/music
```

sudo mount -o **bind** /media/D/music /mnt/music

```

This is more effective than symlinking, it's similar to "jailing" or "sandboxing" where
you stay firmly inside the jail walls. With plain symlink, it's possible to "drop" form
/media/D/music folder to /media/D folder (for example using ftp client) which is
not wanted.


corresponding fstab entry would look like
```

/media/D/music    /mnt/music  none    bind      0    0

```

---

### Post by Lycaon on 2006-07-02
Thanks mlind, though i have accomplished to get a software raid 0 setup working perfectly. The rest i already knew and helped me out. But that fstab entry is very usefull thank you. This is for the next time i want a complete new setup ;)

Now it works though and i won't change much, i dont have much time anyway.

---

### Post by Unknowndeepness on 2006-07-14
I dont know your problem really, but am i correct if i say that you have a symlink to a place outside /glftpd/site?

In that case, it wont work. Glftpd wont go anywhere outside rootdir from your glftpd.conf.

What you can do is thange rootdir to "/". But you'll have to change some more things to.
Look inside the "docs" directory in glftpd, It should be a file called "README.rootdir" there, read that :)

Hope this helps. Otherwise i understood you wrong, or something. :)

---

