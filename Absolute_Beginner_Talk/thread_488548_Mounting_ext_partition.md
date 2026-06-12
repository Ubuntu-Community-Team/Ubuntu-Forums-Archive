---
title: "Mounting ext partition"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by xcom on 2007-06-30
Greetings to all of community.
I decided to try Ubuntu a few moths ago and installed 7.04 Alpha. I had a some trouble setting up the nVidia drivers but it was not that hard. Now everything works great including desktop effects.  Overall I really like what I saw and have decided to keep Ubuntu as my home system. But there are a few things that I could not solve myself so I hope that people of the community can give me a few pointers. So here it goes, I have the following problems:

1. Since I installed Ubuntu 7.04 Alpha, because I wanted new features but I did not want to wait for final  release, I have the following dilemma  now that the final release is out. I am wondering, do I have to reinstall or is it enough to update.
2. When I update the kernel also gets updated so at the boot screen now I have for kernels. How can I have only one kernel at grub and can I just delete the old kernels in the boot folder.
3. When I installed I didn't make separate partition for home folder. But latter I found out it is a cool and practical thing to do. Can I do that now without a reinstall. I have made separate ext3 partition in Gnome partition editor but I don't know how to mount it to home and when I mount it how to keep it that way so it gets mounted every time I start the system.

Best regards.

---

### Post by alan34 on 2007-07-01
Hi welcome

1) Your system should be the latest and greatest already - it automatically updates
     (as long you are the internet)

2) I would just leave this as is but if you want to change
    
    cd /boot/grub
    sudo cp menu.lst menu.backup_01_07_07
    sudo gedit menu.list

    scroll down and look for the entries you don't want to appear the put a "#" 
   (no quotes) in front save and exit and reboot eg as this

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e35f9d3-0bb9-443e-a45d-7242b734a422 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

#title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root		(hd0,10)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e35f9d3-0bb9-443e-a45d-7242b734a422 ro single
#initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,10)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e35f9d3-0bb9-443e-a45d-7242b734a422 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,10)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2e35f9d3-0bb9-443e-a45d-7242b734a422 ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

#title		Ubuntu, memtest86+
#root		(hd0,10)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

 There are lots of other lines in this file do not delete or alter them;)

3) You have to mount the new partion as /home the edit /etc/fstab . I would not mind playing with my system but not yours if you want try


sudo mount /dev/NAMEOFYOURPARTION /home

eg
sudo mount /dev/sda8 /home

look for other threads for editing /etc/fstab

Remember back all files up before editing them good luck

---

### Post by Moop on 2007-07-01
Psychocats has a tutorial on how to create a home partition. 
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by xcom on 2007-07-01
Hi and thanks on your reply, it has been very helpful.
I have used your instructions and solved two problems out of three. The only thing left thats giving me trouble is editing /etc/fstab - there are some strange numbers caled UUID instead partitions and it looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=98844f3e-a873-4dd0-968b-1ef384b684de /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=803001DE3001DBD2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
UUID=b9f8c056-7f5d-46c6-a0f5-2bfa1da5d3c9 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I have added line for my partition: 
/dev/sdb3 /home/files ext3 defaults,errors=remount-ro 0 	1

but it ignores me. I hope I will find it someware, but help would be welcome.

---

