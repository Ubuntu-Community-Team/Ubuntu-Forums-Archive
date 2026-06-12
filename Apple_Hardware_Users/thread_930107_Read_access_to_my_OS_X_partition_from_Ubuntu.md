---
title: "Read access to my OS X partition from Ubuntu"
date: 2008-09-25
forum: Apple Hardware Users
---

### Post by apetresc on 2008-09-25
I've got Ubuntu on a Macbook Pro, and I can mount the OS X partition just fine but for some reason certain directories in /Users (such as the default Music directory, for instance), are not readable from Ubuntu (permissions problems) unless I run as root. I've added the 'users' flag to the /etc/fstab entry, but still no luck. Anyone know how I can grant full read access to those dirs to non-admin users on Ubuntu? 

For reference, here is my /etc/fstab (red highlighting is mine, obviously):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=73e8fe5f-05b3-4ecb-9c2a-cf65ed1d839a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
# UUID=2860-11F4  /media/EFI      system  partition       vfat    utf8,umask=007,gid=46 0 1
# /dev/sda2
[COLOR="Red"]/dev/sda2       /media/Macintosh        hfsplus rw,exec,auto,users      0       0[/COLOR]

# /dev/sda4
UUID=2afbb878-d46a-4bf4-bcc8-045319e5aa58 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I should mention that SOME directories read just fine. It's only a few (mainly the ones that OS X installs with, like Library, Music, Pictures, etc.) which seem not to be available.

Thanks :)

---

### Post by Mizled on 2008-09-28
I'm also having this SAME issue and I can't seem to figure it out. Here is my /etc/fstab

```
###########################################################################
## Macintosh ##############################################################

/dev/sda2 /media/Macintosh hfsplus rw,exec,auto,users 0 0
```

Some help would be appreciated.

---

### Post by cyberdork33 on 2008-09-28
It is due to file ownership. Your Ubuntu user and your OSX user are seen as different users by the systems,

---

### Post by mfox on 2008-09-28
I have the same problem; how does one fix this?  Any way to do it through the Apple side?

---

### Post by cyberdork33 on 2008-09-28
> **mfox said:**
> I have the same problem; how does one fix this?  Any way to do it through the Apple side?
You should be able to edit the permissions on the files in OSX to allow access to all users. Right-Click on files and folders in OSX and select "get info". The permissions pane is near the bottom of the info window.

---

### Post by mfox on 2008-09-29
Thanks, cyberdork; changing permissions on the Mac side did the trick. :)

---

