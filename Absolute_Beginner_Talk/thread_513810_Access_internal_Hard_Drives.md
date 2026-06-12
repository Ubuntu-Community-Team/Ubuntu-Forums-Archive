---
title: "Access internal Hard Drives"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by TheNZDaddy on 2007-07-30
Hi all!

I have a PC with 3 internal hard drives.  One had windows xp on, which I have now replaced with Ubuntu.  The 2nd internal is formatted as EXT3, and the 3rd as NTFS with files saved when using windows.

I can see both the extra drives, but cannot gain read/write permission - only read.  The owner, in Permissions, is shown as Unknown, and as such i can't change the access permissions.  How can I change this?  Please be gentle with the codes used in terminal, as I am real new to this!!

Once I have write permission, i will transfer the folders from the NTFS drive to the EXT3 drive, and format the NTFS to EXT3 for linux use.  Is this a good idea?  I want ALL traces of Windows to be removed!!

---

### Post by nimajiman on 2007-07-31
First make sure the hard drive you are trying to access is mounted somewhere. Say your 2nd internal EXT3 drive is hdb1, then type from terminal:

sudo mkdir /media/somefoldernamehere
sudo mount /dev/hdb1 /media/somefoldernamehere

You should then be able to access those files through nautilus under /media/somefolder... etc

If you have done this and permissions are still 'unknown' then you could try from terminal:

sudo chown -R 1000:1000 /media/somefoldernamehere

That is you are changing ownership of all files and folders from the specified folder up (which is where you mounted the hdb1) to be owned by user 1000 (which should be you if you are the one that install ubuntu) and group 1000 (which is also your group).

If this doesnt work it may require some further options used with the 'mount' command to specify ownership, but i would try this first

---

### Post by aquavitae on 2007-07-31
> **nimajiman said:**
> sudo mount /dev/hdb1 /media/somefoldernamehere
I'd also add options here:
```
sudo mount -o rw,users,uid=1000,gid=1000 /dev/hdb1 /media/somefoldernamehere
```
the uid and gid arguments are to make sure that the permissions of the folder don't change when you mount it.  I'm not to sure exactly what happens, but if the device (/dev/hdb1) is owned by root, It sometimes automatically changed the folder permissions to match.  rw and users means that any user can write to it.  This might be overkill, but it should work.

If you want to automatically mount when you start up you'll need to add it to /etc/fstab, post back if you need help with that.

---

### Post by TheNZDaddy on 2007-07-31
Thanks guys - I'll try that next time I log on - your help is appreciated!

---

