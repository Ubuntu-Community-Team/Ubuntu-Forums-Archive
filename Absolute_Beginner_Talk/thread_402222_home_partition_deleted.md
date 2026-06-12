---
title: "home partition deleted"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by webofunni on 2007-04-05
i am using ubuntu 6.06 , i have a home partition with 9gb ...... yesterday i decided to delete that partition to increase the size of  another ntfs partition and created another home partition at another position in the hard disk ....... but now i am getting gnome error is there any method to correct the error without reinstalling ubuntu .............

---

### Post by LaurelLynn on 2007-04-05
Dear webofunni,

Did you backup your user directory ¨~/¨ before repartitioning?

Gnome keeps hidden files there with all you settings. If they are gone, from a command prompt I would use ¨adduser new-name¨. Then logging in under that user should get Gnome to work.

From there you can delete the origin username, then recreated it with a fresh slate.

Do this from another user though because you always want to have at least one working account (in fact a backup id is a good idea in general).

Laurel Lynn

---

### Post by jvc26 on 2007-04-05
What error are you getting?
Il

---

### Post by ComplexNumber on 2007-04-05
> **webofunni said:**
> i am using ubuntu 6.06 , i have a home partition with 9gb ...... yesterday i decided to delete that partition to increase the size of  another ntfs partition and created another home partition at another position in the hard disk ....... but now i am getting gnome error is there any method to correct the error without reinstalling ubuntu .............
what gnome error are you getting? also, did you write the changes that you made in your partitions back to the MBR? the MBR contains an array of details about the partitons, such as the size of partiton, starting sector, and type of filesystem for each of the partitions. if any of the data is  inconsistant, it won't be able to find some of all of your operating systems.

---

### Post by webofunni on 2007-04-05
laure i have doubt ........ how ubuntu will recognice which one is the new home partition ........... how would i tell it to use this partition as home partition ...........

---

### Post by webofunni on 2007-04-05
hai complex ............. i had installed edubuntu in one partition and get my grub reconfigured ...... thats i think not a problem .........

---

### Post by LaurelLynn on 2007-04-05
Dear webofunni,

The file ¨/etc/fstab¨ tells Ubuntu where to mount home (and all the other partitions).

$ cat /etc/fstab

Gives something like:

/dev/sda7 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 /usr ext2 defaults,errors=remount-ro 0 1
/dev/sda6 /home ext2 defaults 0 2
/dev/sda3 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

The first ¨/dev¨ entry is the device name for the partition. The second entry is the mount point - /home.

For example if I wanted to move my home partition to sda2 I would:

sudo umount /home

Then edit fstab, I could us ¨vi¨ or ¨nano¨ but if I was a ¨gedit¨ kind of gal I would boot from the Live CD to make the change.

I would comment out the current /home entry and add a new one like so:

#/dev/sda6 /home ext2 defaults 0 2
/dev/sda2 /home ext2 defaults 0 2

Then I would:

sudo mount /home   (or reboot if I was on the Live CD)

If there were a problem the old entry is still there so I could set it back if I needed to.

I did something similar recently when I moved /usr to it´s own partition on one of my systems.

Laurel Lynn

---

