---
title: "Root cannot change User or Group"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-07-13
Just setting up Unison and find I have a permissions problem.  Unison fails giving an error log about permissions on the target.  So I looked at the permissions there and find that all the directories on the drive are typically like this

drwxrwx---  2 root plugdev   4096 2007-07-13 15:51 Data


So I thought that this was simply a matter of changing the permissions and say group for either the drive as a whole or the individual directories.   Apparently not.

I tried to delete a directory and create it again but the same user and group were created.

If I log in as root and either use Nautilus or the command line to change either the user or group I always get a permission denied failure.  If I am root I am not sure how I can get a permission denied but I do.

After some exploration on google I see that people with similar problems should look at their fstab entries.  All of mine are the same but this relates to the drive in question 

# /dev/sdb5

UUID=45F6-5EE5  /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1

Any suggestions of what this problem may be?

Or even how to fix it :)

---

### Post by BobCFC on 2007-07-13
Basically attributes such as rwx permission and owners of individual files can only be set on linux type partitions such as xfs, ext2, ext3 reiserFS etc..

FAT32(vfat) and NTFS are set once for the whole drive in fstab using umask for rwx and gid for owner.

---

### Post by expatCM on 2007-07-13
Thank you for explaining that ... I did not know.  So at some stage when I give up dual booting I guess I will be best advised to convert the drives to ext3.  No doubt that will be a whole bundle of fun.

Not sure that I have got the hang of this though.  I had a look in the ubuntuguide at this link
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
and found that it was suggested to make changes to fstab.  So I did ...  I ended up with this line. 
# /dev/sdb5
UUID=45F6-5EE5  /media/sdb5     vfat    iocharset=utf8,umask=000,gid=1000  0    0

The effect has been to change the group to root (not user 1000) but leave the user as root.  Transfers to the drive are still blocked.

So I was wondering what I have not done........   Yes I did run  sudo mount -a before testing.

---

### Post by zanglang on 2007-07-13
How about trying this?
> UUID=45F6-5EE5 /media/sdb5 vfat defaults, utf8,umask=000 0 0

---

### Post by expatCM on 2007-07-13
Tried that and it defaults back to root.   What is interesting is that sudo mount -a does zip in this case but a reboot puts the changes into place.  The inclusion of gid=1000 did take effect on reboot.

I now do not think that the problem with with fstab, I think it is with Unison.  I found only one post on google but it is close enough to what I experience to be the same
[http://lists.seas.upenn.edu/pipermail/unison-hackers/2005-October/000277.html](http://lists.seas.upenn.edu/pipermail/unison-hackers/2005-October/000277.html)

Not as if I understand it all though but it sounds like there is no fix.   

So I guess I have two options.  One is to change the drive from FAT32 to ext3 ...  and I have no idea how to do that.  Second is to try a different program and see what happens.

---

### Post by BobCFC on 2007-07-14
My favourite is XFS.  Apart from sounding cool it is supposed to have the best performance.. it was written by Silicon Graphics for renderfarms and comes from proper UNIX.

The only disadvantage is that you can't shrink partitions, but they can grow.

---

### Post by expatCM on 2007-07-14
XFS ...  hmmm ... probably not (but thanks for suggesting it).  I am really totally chicken since when I dig myself a hole I am the only person who can get out of it.

---

