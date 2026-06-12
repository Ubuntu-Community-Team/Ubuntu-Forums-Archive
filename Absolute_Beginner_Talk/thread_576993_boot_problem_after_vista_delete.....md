---
title: "boot problem after vista delete...."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-15
I thought something like this might happen (if something is going to go wrong at boot then im the person to find out! lol) i deleted my vista partition from the ubuntu live cd and then extended my ubuntu partition to cover the whole drive after i completed this i rebooted and i got something like  this error

```
Boot sector invalid press h to try again
```

so i used the live cd and then used the "boot from hd" option and every thing's fine so i dont really know what i have done....lol

Oh also how do i remove the old vista boot option from grub? (assuming i can fix the first problem..)

---

### Post by jpyanowski on 2007-10-15
You will have to reinstall grub

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by MatthewPlanchard on 2007-10-15
Hi,

Assuming everything (including the GRUB) is working properly, after repartitioning you will need to do two things:
update your fstab file so that everything boots correctly!
to do this, you'll want to use

```
sudo gedit /etc/fstab
```

to access the file with write permissions and then

```
fdisk
blkid
```

to get the necessary information for the fstab. MAKE SURE THE UUID's MATCH.

Next, you'll want to edit your GRUB to remove the Windows partition.

You can do this by

```
sudo gedit /boot/grub/menu.lst
```

Find the partition you want to delete from the GRUB startup menu (in this case the Windows partition) and either delete it or hash it out (precede each line with a #).

Note that with the menu.lst file you can also change the name of your Ubuntu partition from Ubuntu Kernel 12341234lksdjhfa
to something like
My Awesome Ubuntu Desktop

Good luck!

---

