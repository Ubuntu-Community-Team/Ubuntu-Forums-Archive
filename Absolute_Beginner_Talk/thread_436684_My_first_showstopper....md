---
title: "My first showstopper..."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by dpzektor on 2007-05-08
Been running Ubuntu for about a month now, no problems...until tonight:

I purchased a 320GB IOmega external USB HD about a week ago. The unit came pre-formatted Fat32, and worked right off the bat when connected in Ubuntu. But, tonight I tried to copy over some files that were over 4GB. I completely forgot about Fat32's file size limitation, and of course the second the copies hit 4GB the file manager closed out. 

So, I figured I'd format the drive EXT3, as I do not needto use it in a Windows machine. I used Gparted, and all worked well (or so I think?). I reboot, and the drive is auto mounted. Here's the kicker tho, I have no permissions to write to it! I enetered the drive as root, and of course all works fine there and I can copy files and do whatever. But, I need it to work with my normal account. Does anybody have a clue as to what I can do (how I can) adjust permissions to let myself r/w to this drive normally?

---

### Post by Skrynesaver on 2007-05-08
add "rw,users" to the attributes for the device in /etc/fstab (or create an fstab entry for it if none exists.  This will allow all authenticated users  write access to it

---

### Post by ctsdownloads on 2007-05-08
Skrynesaver : I am interested in this as well. Can you outline clearly where this goes in the fstab file?

Btw dpzektor, you goto Applications, Accessories and then terminal. From there, copy and then right click paste:
> 
sudo gedit /etc/fstab

...to get to the needed file he is talking about.

---

### Post by dpzektor on 2007-05-08
That worked. Thanks for the help. Out of curiosity, why is this needed? I set permissions on the drive as root initially and that did not work. Either way, thanks for the heads up!

---

### Post by Skrynesaver on 2007-05-08
an fstab entry consists of> 
IDENTIFIER   MOUNT_POINT   FS_TYPE OPTIONS FS_FREQ FS_PAA_NO
IDENTIFIER: unquely identifies a file system
MOUNT_POINT: Where to mount the filesystem
FS_TYPE: The filesystem type
MOUNT_OPTIONS: options to give the mount command, this includes the following options:
> 
async - All I/O to the file system should be done asynchronously. This can improve system performance by doing "lazy writes" but could be dangerous for removeable drives such as floppy disks.

 atime - Update inode access time for each access. This is the default.

 auto - Can be mounted with the -a option.

 defaults - Use default options: rw, suid, dev, exec, auto, nouser, and async.   

dev - Interpret character or block special devices on the file system.   

exec - Permit execution of binaries.   

_netdev - The filesystem resides on a device that requires network access (used to prevent the system from attempting to mount these filesystems until the network has been enabled on the system). 

noatime - Do not update inode access times on this file system (e.g, for faster access on the news spool to speed up news servers). 

noauto - Can only be mounted explicitly (i.e., the -a option will not cause the file system to be mounted).   

nodev - Do not interpret character or block special devices on the file system.   

noexec - Do not allow execution of any binaries on the mounted file system. This option might be useful for a server that has file systems containing binaries for architectures other than its own. 

nosuid - Do not allow set-user-identifier or set-group-identifier bits to take effect. (This seems safe, but is in fact rather unsafe if you have suidperl(1) installed.) 

nouser - Forbid an ordinary (i.e., non-root) user to mount the file system. This is the default.   

remount - Attempt to remount an already-mounted file system. This is commonly used to change the mount flags for a file system, especially to make a readonly file system writeable. It does not change device or mount point. 

ro - Mount the file system read-only.   

rw - Mount the file system read-write.   

suid - Allow set-user-identifier or set-group-identifier bits to take effect.   

sync - All I/O to the file system should be done synchronously.   

user - Allow an ordinary user to mount the file system. The name of the mounting user is written to mtab so that he can unmount the file system again. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line user,exec,dev,suid). 

users - Allow every user to mount and unmount the file system. This option implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option line users,exec,dev,suid).

FS_DUMP: leave as zero, overly complicated filesystem backup (good on servers)
FS_PASS_NO: How often to check the filesystem on boot

That should answer both questions fully, off to do some paying work now ;)

---

### Post by LaurelLynn on 2007-05-08
It is needed, because if root owns the drive it owns all the files/folders on it. With "rw,users" your letting all users write to the drive. Permissions then are based on who creates the files/folders.

For example, if I have a folder that contains a file you own. You can't read it, inspite of the fact that it is yours, unless I give you read access to the folder.

---

### Post by dpzektor on 2007-05-08
Wow, thanks for the information. The permission system in Linux is quite advanced, more than I initially thought it was. Again, thanks all!

---

