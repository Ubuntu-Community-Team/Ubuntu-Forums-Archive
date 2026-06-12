---
title: "Issue with Shutdown sequence / unclean umount of root partition"
date: 2011-10-04
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Argos8 on 2011-10-04
Hi,

I have installed ubuntu 11.04 on my ASUS EEEPC 901.
Because it works with internal SSD Drives I chose to
install it on a ext2 (non journaling) file system and to 
prepare /etc/fstab like that:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    noatime,nodev,noexec,nosuid 0 0

/dev/sda2 /   ext2   noatime,nodiratime,errors=remount-ro 0 1

tmpfs /tmp tmpfs defaults,noatime,nodiratime,nosuid,size=25%,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,size=25%,nodiratime 0 0


After Installation the system actualy worked fine until I noticed that it performs fsck on root partition at every boot because it was &quot;not unmounted clean&quot;. I suppose this has something to do with the shutdown/restart sequence though not sure.

Can anyone reproduce this or knows what could possibly cause that problem?

Thanks for your answers.     

EDIT: Hey guys, I solved the problem after I found this  [http://www.linuxforums.org/forum/ubuntu-linux/147634-solved-ubuntu-does-not-umount-filesystems-shutdown-restart.html#](http://www.linuxforums.org/forum/ubuntu-linux/147634-solved-ubuntu-does-not-umount-filesystems-shutdown-restart.html#)  executing  $ sudo update-rc.d -f umountroot remove $ sudo update-rc.d -f umountfs remove $ sudo update-rc.d -f umountnfs.sh remove $ sudo update-rc.d -f halt remove $ sudo update-rc.d -f reboot remove  $ sudo update-rc.d umountnfs.sh start 31 0 6 . $ sudo update-rc.d umountfs start 40 0 6 . $ sudo update-rc.d umountroot start 60 0 6 .  $ sudo update-rc.d halt start 90 0 . $ sudo update-rc.d reboot start 90 6 .  corrects the problem described above. Seems like I screwed up my shutdown services somehow, which is strange because I didn't do anything to them but anyway the problem is now solved.

---

