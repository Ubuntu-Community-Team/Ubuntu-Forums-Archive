---
title: "recovering files from HFS leopard install using liveCD"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by javaholic on 2009-04-08
Is it possible to recover the files found on a apple mac osx leopard harddrive (HFS file system) using a 8.10 livecd.

I have got to the point where i can see that the files on the drive in question are associated to user 502 but can't seem to view them or copy them at this point even though i have tried to chown them to the root user.
If i can get to them in this way how do i do it.

All i want to do is copy the files to a pendrive so i can be happy with formatting the entire drive.

---

### Post by tgalati4 on 2009-04-08
You should be able to read HFS partitions with Ubuntu.  You may need to fschk.hfs if the drive is corrupted.  You will need to disable journaling (going from hfs+ to hfs) to be able to write/repair the drive with Ubuntu.  This can be done with a command line utility or Disk Utility in OS X.

---

### Post by tiresia on 2009-04-08
Start from the LiveCD, open a Terminal and run Nautilus with gksudo (because as normal user you can't access those files)
```
gksudo nautilus
```
You will be able to backup everthing you need

---

### Post by cyberdork33 on 2009-04-08
We've actually found that you usually need to open two root-enabled nautilus windows to drag files between, then you can chown the copies.

(PS you can't chown the files on the HFS+ partition because you cannot write to that partition)

---

### Post by javaholic on 2009-04-08
I figured how to do it as stated above essentially but this is a really slow process.I had hoped i would be able to create a share and copy the contents over the network cause 40gs of music and video that they want saved will take forever to do with just one 4GB pendrive.

I got as far as trying to log in via samba to share trying to log in as root but failing i think it is reverting me to Guest user.

my guess is that i would have to do sudo nautilus and then try to access the files to copy with:

smb://root@system_with_files_ip_address/

But i failed in all my early tests.

Would have been useful if it had worked.

---

### Post by cyberdork33 on 2009-04-08
> **javaholic said:**
> I figured how to do it as stated above essentially but this is a really slow process.I had hoped i would be able to create a share and copy the contents over the network cause 40gs of music and video that they want saved will take forever to do with just one 4GB pendrive.

I got as far as trying to log in via samba to share trying to log in as root but failing i think it is reverting me to Guest user.

my guess is that i would have to do sudo nautilus and then try to access the files to copy with:

smb://root@system_with_files_ip_address/

But i failed in all my early tests.

Would have been useful if it had worked.
I think as long as you are using a root nautilus window, you can copy to a samba share that you connect via Guest (or whatever else).

You can always mount your samba share in the file system, then navigate to the folder in your root nautilus window.

---

