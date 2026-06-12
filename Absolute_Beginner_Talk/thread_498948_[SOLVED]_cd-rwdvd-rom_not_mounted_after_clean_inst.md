---
title: "[SOLVED] cd-rw/dvd-rom not mounted after clean install"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-12
What give with the optical drives?
I know we don't want to violate copyright, but geez, developers/tester/Shuttleworth, give me a break.

After my friend's toshiba satellite 1905-s304 had XP blow up, I convinced him to try ubuntu. I installed the entire drive under it.

Now I have his laptop at home, trying to get wireless up for him and I need the optical drive (cd-rw/dvd-rom) and it won't read the drive even from a cold boot, with the bios set to atapi first, etc.

What gives? Ubuntu should be better than this. I've looked around for about 60 minutes and found nothing but zero response posts about "drive not mounted" and "probably no media".

I've switched /etc/fstab's line about cdrom back and forth from sdc0 to hda, and had nothing work.

This wouldn't be such a burden if I hadn't the same problem or very similar problem. Unless I cold boot with media in the cd drive Ubuntu has no clue that there is an active, working optical drive in the box. Shame!

If anybody reading this can suggest something else, I'm game.

I'm editing this post, because I found the exact same problem at another forum with ZERO responses. What's up with this?

From: 
[http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html](http://help.lockergnome.com/linux/installed-ubuntu-04-detect-cdrom0-help-ftopict423119.html)

 Posted: Wed May 16, 2007 5:00 pm
Post subject: once installed ubuntu 7.04 doesn't detect cdrom0. please help?
Archived from groups: aus>computers>linux (more info?) 	
Hi
I'm a newbie having trouble getting my installation of ubuntu ver 7.04
to detect my dvd combo. (the same one it was installed from.)

It can boot the system but once the system is booted from the hdd it
cannot detect a cdrom/dvd drive.
disk mounter 2.18.0 only shows a floppy as available to mount. nothing
else is listed

there is a /dev/scd0 file
a /media/cdrom0 folder
/mnt is empty should it be?

fstab as below:
#uto /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd / reiserfs notail 0 1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home reiserfs defaults 0 2
# /dev/sda1
UUID=28D06453D06428F0 /windows ntfs defaults,nls=utf8,umask=007,gid=46
0
1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user, noauto 0 0

this is the mount table:
#uto /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd / reiserfs
notail 0 1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home reiserfs
defaults 0 2
# /dev/sda1
UUID=28D06453D06428F0 /windows ntfs
defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none swap sw
0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

the permission details for /media/ :
#uto /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=8ad32a93-dd79-4172-8a8f-305534a525fd / reiserfs
notail 0 1
# /dev/sda7
UUID=ed1b698b-fa37-4bc1-80f6-1333ea03ae6f /home reiserfs
defaults 0 2
# /dev/sda1
UUID=28D06453D06428F0 /windows ntfs
defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=791017d2-de08-446b-972b-2a361797c3c0 none swap sw
0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0



can anyone help?
its probable so easy if I only knew...
as all the files seem to be present, I suspect it is a permission
issue..
veets

---

### Post by Inxsible on 2007-07-12
> **Mark_in_Hollywood said:**
> What give with the optical drives?
I know we don't want to violate copyright, but geez, developers/tester/Shuttleworth, give me a break.

After my friend's toshiba satellite 1905-s304 had XP blow up, I convinced him to try ubuntu. I installed the entire drive under it.

Now I have his laptop at home, trying to get wireless up for him and I need the optical drive (cd-rw/dvd-rom) and it won't read the drive even from a cold boot, with the bios set to atapi first, etc.

What gives? Ubuntu should be better than this. I've looked around for about 60 minutes and found nothing but zero response posts about "drive not mounted" and "probably no media".

I've switched /etc/fstab's line about cdrom back and forth from sdc0 to hda, and had nothing work.

This wouldn't be such a burden if I hadn't the same problem or very similar problem. Unless I cold boot with media in the cd drive Ubuntu has no clue that there is an active, working optical drive in the box. Shame!

If anybody reading this can suggest something else, I'm game.

Try commenting the fstab entry for the cd drive. CD drives are removable media and should be mounted when you put in a cd/dvd 
See if that works

---

### Post by Mark_in_Hollywood on 2007-07-12
Looking over the Place/Computer/CD-RW-DVD-ROM under Properties and Permission the drive's owner is: unknown

What fixes that?

---

### Post by Mark_in_Hollywood on 2007-07-12
Thank you for the idea, I commented out the line, rebooted and same prob.

---

