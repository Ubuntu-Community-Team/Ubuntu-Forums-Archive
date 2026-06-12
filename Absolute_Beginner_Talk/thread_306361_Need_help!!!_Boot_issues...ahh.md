---
title: "Need help!!! Boot issues...ahh"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by studio472 on 2006-11-24
Heres what happened...

Have Windows XP Home...
Partitioned HD and Installed Ubuntu
Dual boot was fine, I could select either Ubuntu or Windows to boot from...
I got cocky, and from windows, deleted the partition with Ubuntu (and the swap)...
Now it doesn't do anything during boot up-I think because they'res no ubuntu for it to find.
I'm fairly certain the boot file is on the original partition, ultimately, I just want to get windows back to normal (prefferably without losing it)

What I've tried...
Tried re-installing Ubuntu (the way It was when it worked as a dual boot) - Now its not letting me edit the HD partition (I have NOT tried reformatting it)... 
Right now, the only way the system will run is via the Ubuntu Live-CD...
So all editing has to be done via a NON-installed Ubuntu... 
Please help!

---

### Post by rlozano on 2006-11-24
> **studio472 said:**
> Heres what happened...

Have Windows XP Home...
Partitioned HD and Installed Ubuntu
Dual boot was fine, I could select either Ubuntu or Windows to boot from...
I got cocky, and from windows, deleted the partition with Ubuntu (and the swap)...
Now it doesn't do anything during boot up-I think because they'res no ubuntu for it to find.
I'm fairly certain the boot file is on the original partition, ultimately, I just want to get windows back to normal (prefferably without losing it)

What I've tried...
Tried re-installing Ubuntu (the way It was when it worked as a dual boot) - Now its not letting me edit the HD partition (I have NOT tried reformatting it)... 
Right now, the only way the system will run is via the Ubuntu Live-CD...
So all editing has to be done via a NON-installed Ubuntu... 
Please help!

your windows MBR was actually written over by GRUB. it's still there dont panic. get a utility that will restore your windows MBR. or you can use fdisk /mbr (if im not mistaken.)

go get yourself a utility to restore your MBR and all will be fine. or another way is, get a grub CD or diskette, boot with grub and manually load your windows OS.

---

### Post by confused57 on 2006-11-24
Here's how to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You'll need a Windows install cd(not a recovery one), bootup with the cd...press "r" for recovery, then **fixmbr**...or you can make a Win98SE oem boot floppy(which uses **fdisk /mbr**) from bootdisk.com, as described in the link.

---

### Post by cromestant on 2006-11-24
Actually just boot your xp install cd, get to the partitioning screen, then reboot ( my cd at that point already has overwritten mbr

then reboot, you should see windows booting

then boot with ubuntu live cd,  
open a  terminal, 
mkdir /mnt/ubuntu
mount /dev/hda /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

then reinstall grub : 
apt-get install grub 
or

cd /boot/grub
grub

 root (hd0,0)
 setup (hd0)
 quit 


That should do it
unmount your mounted points

/mnt/ubuntu/proc
/mnt/ubuntu/dev
/mnt/ubuntu

and you should be done

hope this helps

---

