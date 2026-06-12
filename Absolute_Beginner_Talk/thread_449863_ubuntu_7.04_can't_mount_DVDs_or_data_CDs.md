---
title: "ubuntu 7.04 can't mount DVDs or data CDs"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by veetz on 2007-05-20
Hi
I'm a newbie having trouble getting my installation of ubuntu ver 7.04
to detect my dvd combo. the same one it was installed from.

It can boot the system but once the system is booted from the hdd it
cannot detect a cdrom drive.
disk mounter 2.18.0 only shows a floppy as available to mount. nothing
else is listed

More testing: audio CDs play. (sound juicer)
              data cds are not mounted (permissions? wrong filesystem(fat32)? hummm..)
              the origional Ubuntu 7.04 DVD is not detected. It was installed from this DVD.
              DVD movies are undetected

there is software for DVD playing/burning etc: gxine, DVDshrink, cd/dvd writer gnomebaker

ah!  So much I just don't know yet...

there is a:      /dev/scd0 file 
                       /media/cdrom0 folder(file?)
        and /mnt is empty. should it be?

fstab is as below:
#uto /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                       <dump>  <pass>
proc            /proc           proc    defaults                           0       0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd /  reiserfs notail               0       1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home reiserfs defaults          0       2
# /dev/sda1
UUID=28D06453D06428F0 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0    1      1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none swap sw                      0       0
/dev/scd0  /media/cdrom0   udf,iso9660 user,noauto                          0       0
/dev/fd0   /media/floppy0  auto  rw,user,   noauto                          0       0

this is the mount table:
#uto /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                        <dump>  <pass>
proc            /proc           proc    defaults                           0       0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd /  reiserfs      notail          0       1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home     reiserfs  defaults     0       2
# /dev/sda1
UUID=28D06453D06428F0 /windows  ntfs defaults,nls=utf8,umask=007,gid=46    0       1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none   swap  sw                  0       0
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto                     0       0
/dev/fd0   /media/floppy0  auto  rw,user,noauto                            0       0

the permission details for /media/ :
#uto /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                        <dump>  <pass>
proc            /proc           proc    defaults                            0       0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd /   reiserfs notail               0       1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home reiserfs  defaults          0       2
# /dev/sda1
UUID=28D06453D06428F0 /windows  ntfs  defaults,nls=utf8,umask=007,gid=46    0       1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none  swap  sw                    0       0
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto                      0       0
/dev/fd0   /media/floppy0  auto  rw,user,noauto                             0       0
 


can anyone help?
its probable so easy if I only knew...
veets

PS:
I just installed ver 6.06 onto an older laptop. perfect . everything works! The cdrom 
is detected and an icon appears in the bar at the top. when I "dock" the dvd/cd reader
 the os doesn't detect it any more...any work around? Could this be a related problem?



thanks in advance 
veetz

---

