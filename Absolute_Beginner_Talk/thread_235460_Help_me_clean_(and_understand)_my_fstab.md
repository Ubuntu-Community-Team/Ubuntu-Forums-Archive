---
title: "Help me clean (and understand) my fstab"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-08-13
I'm not a total newbie, but there are still some things that I'm not familiar with. One of them is fstab. For the past months, I've accumulated some modifications to fstab that I have forgotten why I added or what they do. So my fstab looks like a mess. I'm not even sure if they're the correct or default values. They just worked, and didn't bother trying to find out how/why. I'm wondering if some more experienced users could help me clean it up a bit, and probably understand it. 

Here's my fstab. I've added some comments to indicated what filesystem the partitions use and which ones I want to mount at startup.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0

# / (root) and swap partitions
/dev/hdb1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/hdb2 none swap sw 0 0

# Windowx XP (NTFS)
/dev/hda1 /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,ro,user 0 1

# FAT32 shared partition
# needs to be mounted at startup and files belong to me 
/dev/hda3 /media/idagurl vfat defaults,utf8,umask=007,uid=1000,gid=1000,auto,rw,owner 0 1

# /home partition
/dev/hdb3 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2

# hdb4 is an extended partition containing hdb5 and hdb6

# extra partition (for other distros)
/dev/hdb5 /media/other ext3 user,defaults,atime,auto,rw,dev,exec,suid 0 2

# FAT32 shared partition
# needs to be mounted at startup and files belong to me
/dev/hdb6 /media/shared vfat defaults,utf8,umask=007,uid=1000,gid=1000,auto,rw,owner 0 1

#CD-RW
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

#CD-ROM
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0


Thanks for anyone who would have the patience and time for this.

---

### Post by Cyhatch on 2006-08-13
Hrm. I don't think many will have the nerve to explain *everything*. Did you try searching *man fstab* for the particular values you don't understand?

(Or maybe you could list those here.)

---

### Post by xpod on 2006-08-13
Theres a decent explanation right at the top of the page if you just type"fstab" in google.
I suppose you mabey have but just a thought(still trying to get my own head round it)

---

### Post by Jucato on 2006-08-13
I did try reading the man pages for the options. I understand some of them. What I'm really not sure about is the proper combinations of options.

For example this line here:
> 
/dev/hdb6 /media/shared vfat defaults,utf8,umask=007,uid=1000,gid=1000,auto,rw, owner 0 1


When I first installed Kubuntu, this partition was only accessible by root. I do remember putting the uid and gid values there to make it accessible to my user, but I'm not sure if that's the proper way to do it.

Btw, the description of the options on fstab are actually in the man page for "mount", which is what I read.

I'm not asking everything to be explained. That's obviously too much. Maybe just a pointer in the proper direction about the combination of options, and I'll be happy to do my own research.

Thanks a bunch!

---

### Post by xpod on 2006-08-13
Im just watching so i too can mabey understand a bit more....sorry

---

### Post by infoseeker on 2006-08-13
Some info here

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bonzodog on 2006-08-13
here's what I think it should look like:
```

proc         /proc       proc    defaults                                 0 0
/dev/hdb1    /           ext3    defaults,errors=remount-ro,noatime       0 1
/dev/hdb2    swap        swap  				                  0 0
/dev/hdb3    /home       ext3    defaults,noatime	                  0 2
/dev/hda1    /media/hda1 ntfs    defaults,nls=utf8,umask=000,auto,ro,user 0 1
/dev/hdb5    /media/other ext3	   user,defaults,noatime 	          0 2
/dev/hda3    /media/idagurl vfat     defaults,utf8,umask=000,auto,user    0 1
/dev/hdb6    /media/shared  vfat     defaults,utf8,umask=000,auto,user    0 1
/dev/hdc     /media/cdrom0  udf,iso9660  user,noauto              0 0
/dev/hdd     /media/cdrom1  udf,iso9660  user,noauto  		  0 0

```

The exec,rw,suid options are not needed, as that is what defaults does.
also, I have switched atime to noatime, as that will reduce access times to the Hard disk, as it will prevent it from recording all accesses to the hard disk, and only record writes, not reads. The option should not even be in the CDROM lines.

---

### Post by Cyhatch on 2006-08-13
Fenyx, I guess that line is OK.

Options are set from left to right. 'uid' and 'gid' set user 1000 (you, probably) as the owner of the device, then 'owner' allows user 1000 to mount the drive. Also, it unsets 'uid' and 'dev' that were previosly set by 'defaults'. You should have that in mind.

'rw' and 'auto' aren't necessary here: they're already set by 'defaults'.

---

### Post by ChadMMc on 2006-08-13
Just a thought. Have you checked the info pages?

```
info fstab
```

It seems to give a full description of each of the fields. Not sure if it will help.

---

### Post by Jucato on 2006-08-13
Heheh! this is exactly what I was talking about. I didn't know, for example, that some options were duplicated.

@bonzodog: thanks for that! will I still have read/write access to the vfat partitions (hda3 and hdb6)?

---

### Post by bonzodog on 2006-08-13
if you just change the word 'owner' to 'user' it will allow users to mount/unmount partitions.

---

### Post by Jucato on 2006-08-13
cool! thanks! I'm gonna try it out :-D

EDIT:
Thanks! It worked. So let me get this straight:
user - any user can mount/unmount it, and the partition will be readable/writeable by any user?
owner - only root can mount/unmount it and the partition will belong to root, so only root can read/write from/to it?

Because that's what happened when I changed "user" to "owner" for the vfat partitions.

Thanks again!

---

### Post by Jucato on 2006-08-13
Er... I spoke too soon. I copied the fstab you gave (with a minor correction in the swap line). I thought everything was wokring fine, but when I restarted, /dev/hda3 and /dev/hdb6 both belong to root, and I have no read/write access to them.

How do I make these partitions belong to my user so I could have read/write access?

---

### Post by Cyhatch on 2006-08-13
Fenyx, here's what man mount says about user and users:

```
              user   Allow  an  ordinary  user  to mount the file system.  The
                     name of the mounting user is written to mtab so  that  he
                     can  unmount  the file system again.  This option implies
                     the options noexec, nosuid, and nodev (unless  overridden
                     by   subsequent   options,   as   in   the   option  line
                     user,exec,dev,suid).

              users  Allow every user to mount and unmount  the  file  system.
                     This option implies the options noexec, nosuid, and nodev
                     (unless overridden  by  subsequent  options,  as  in  the
                     option line users,exec,dev,suid).
```

If you have 'user' set, then at boot time root mounts the filesystem. You either need 'user**s**' so that anyone can mount it; or leave it the way you had: with 'uid', 'gid' and 'owner'. The latter is more secure. Also, keep the umask=007 part (as opposed to umask=000). Apart from looking cool, it protects you from that Nasty.sis virus that creates an account in your box and destroys everything. 

> **Fenyx said:**
> I didn't know, for example, that some options were duplicated.

Yeah. They kind of "stack" upon one another.

---

