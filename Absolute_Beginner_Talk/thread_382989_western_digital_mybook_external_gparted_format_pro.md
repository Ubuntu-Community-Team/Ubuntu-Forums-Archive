---
title: "western digital mybook external gparted format problem"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-12
i have a new western digital 500g external mybook drive i am trying to format.  i am using gparted and i choose to unmount the drive and delete the contents.  i hit apply and all goes well.  then i choose format with ext3 and i get . . . .

/dev/sdc1 is mounted; will not make file system here!

well, i all ready unmounted it, but when i hit apply to format the drive auto mounts again and the contents pop up.  any ideas?

also, since i unmount and deleted partition, shouldn't all the contents of the drive have been wiped?  it seems as though the contents were unaffected even though i delete the partition and exited gparted.

---

### Post by dbbolton on 2007-03-12
have you tried any other filesystem types ?

---

### Post by DerArzt on 2007-03-12
I would recommend trying the gparted live cd that can be found here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by larrybrazos on 2007-03-12
i have tried other filesystems, thought it might be a ext3 issue, but same issue.  instead of the live cd and gparted, can i just cut out the gui and someone hit me with a command to format this bad boy?

i don't care if it is unreadable by windows.  i want one big parition with a linux filesystem.

i think there is an issue with it trying to mount itself when gparted trys to format it, so i figure there would be some switch in a command to stop it from trying to mount . . .

---

### Post by larrybrazos on 2007-03-15
i plugged this drive in to my laptop running xp and decided it was probably best to just use ntfs so if i ever needed to use the drive on a windows machine i wouldn't have any problems.

so, a different question . . .

i couldn't read another hard drive i have during an ssh session from work, so i just hit it with

sudo chmod 777 /media/Media

is this a bad way to get permission to see the drive?

---

### Post by ollyshaw on 2007-03-23
I am having exactly the same problem with my mybook. Delete the partion and it comes back to life! Bizarre! Any help appreciated.

Olly

---

### Post by kpkeerthi on 2007-03-23
1. Unmount the drive:
sudo umount /dev/hdb1  (or whatever it was mounted as. Use 'sudo fdisk -l' to check)

2. Create partition:
mkfs /dev/hdb1 -t ext3

---

### Post by ollyshaw on 2007-03-23
Thanks kpkeerthi!

Also this post works too.

[http://www.ubuntuforums.org/showthread.php?t=380817&highlight=disable+automount](http://www.ubuntuforums.org/showthread.php?t=380817&highlight=disable+automount)

Cheers,

Olly

---

