---
title: "Automounting with correct priveleges"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ace214 on 2007-07-23
I set up one of my hard drives to automount in fstab with
```
/dev/hda1	/media/MMMM	vfat	rw,user,auto	0	0
```
but it mounts so that only root can change files. and when i sudo and try to change the permissions of the folder it won't let me. i thought the user option would let me do everything but it won't even let me unmount the volume.

---

### Post by bernied on 2007-07-23
This is from the command 'man mount':
```
Mount options for fat
       (Note: fat is not a separate filesystem,  but  a  common  part  of  the
       msdos, umsdos and vfat filesystems.)

       blocksize=512 / blocksize=1024 / blocksize=2048
              Set blocksize (default 512).

       uid=value and gid=value
              Set the owner and group of all files.  (Default: the uid and gid
              of the current process.)

       umask=value
              Set the umask (the bitmask  of  the  permissions  that  are  not
              present).  The default is the umask of the current process.  The
              value is given in octal.

       dmask=value
              Set the umask applied to directories only.  The default  is  the
              umask of the current process.  The value is given in octal.

       fmask=value
              Set the umask applied to regular files only.  The default is the
              umask of the current process.  The value is given in octal.
```
I know this is difficult to understand, here is some tentative translation...

- with auto set, user will have no effect, as it will be mounted by root at startup, so only root will be able to unmount it.
- if you don't set any user or group for the filesystem (fat filesystems have no real permissions), then it will adopt those of the process that mounts it - so it will be owned by root
- likewise for permissions, if you don't specify a umask, it will choose that of root [EDIT] umask specifies the revers of the permissions, 002 means read/write/execute for user and group, read/execute for other[/EDIT]

So, depending on who you want to have access, and how much, you should use some more options in that fstab entry. I'd suggest adding 'gid=100,umask=002'. This should give read/write access to all users in the 'users' group. You can add yourself and others to this group in Administration - Users and Groups. But you may need to log out and back in again for this to take effect. 

If you want users to be able to mount and unmount the device, then take out the word 'auto' from the options and make sure that 'users' have read/write permission over the mountpoint:
```
sudo umount /media/MMMM
sudo chown root:users /media/MMMM
sudo chmod u+rw /media/MMMM
mount /media/MMMM
```

See if that works...

---

### Post by ace214 on 2007-07-24
That worked. Thanks a lot.

---

