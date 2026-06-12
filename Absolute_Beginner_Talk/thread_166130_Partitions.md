---
title: "Partitions"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-04-25
Hello,
I'm a bit of a noob, so bear with me. I just wiped out a Small Business Server and installed Ubuntu. My machine has two hard drives, the smaller of which has the OS installed on it. The other hard drive has no partitions whatsoever. I need to partition it, but I don't know how. I went to the Disks Manager, but the buttons for creating a partition are greyed out.

Any ideas?

---

### Post by joshrobinson on 2006-04-25
open up synaptic and search for QTparted (system > administration > synaptic)

install it, then it should be in applications > system tools

that should let you add your partitions

---

### Post by Sef on 2006-04-25
You can't partition on a hard drive when it is mounted.   What you need to do is get a live cd and use the partitioner from there.  Applications > Accessories > GParted.  That will allow you to partition the hard drive.


> open up synaptic and search for QTparted (system > administration > synaptic)

install it, then it should be in applications > system tools

that should let you add your partitions

I don't think that will not work because the hard drive to be partitioned is mounted.

---

### Post by gantww on 2006-04-25
Thanks. It worked.

---

### Post by gantww on 2006-04-25
[QUOTE=gantww]Thanks. It worked.[/QUOTE]

Whoops. It worked all right, but I can't figure out how to get to it. What now?

---

### Post by gantww on 2006-04-25
[QUOTE=gantww]Whoops. It worked all right, but I can't figure out how to get to it. What now?[/QUOTE]

But I saw the quote above about formatting not working when the drive is mounted. I went back into my handy dandy disk application and gave it a mount point and now it works. Will it still be there after a reboot?

---

### Post by jimrz on 2006-04-25
in terminal type:

sudo mkdir /media/<[COLOR="Red"]**your choice of name for partition**[/COLOR]>
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

then append a line something like this,using your choice of name / file system and the correct hd designation for your partion:

/dev/hd[COLOR="Red"]**x**[/COLOR][COLOR="Red"]**x **[/COLOR]    /media/<[COLOR="Red"]**your choice**[/COLOR]>[COLOR="White"]_____[/COLOR][COLOR="White"]_[/COLOR]ext3[COLOR="White"]_____[/COLOR]    defaults[COLOR="White"]___[/COLOR]0[COLOR="White"]_____[/COLOR]2 

this will make it mount each time you spin'er up

if you formatted as ntfs or vfat there will be diferent values for the fstab addition, which may be found [[COLOR="Sienna"]**_here_**[/COLOR]]("http://www.ubuntuguide.org/#automountfat")

---

### Post by jazzmuzik on 2006-04-25
[QUOTE=gantww]But I saw the quote above about formatting not working when the drive is mounted. I went back into my handy dandy disk application and gave it a mount point and now it works. Will it still be there after a reboot?[/QUOTE]

To make your new drive accessible each time you boot up, you need to add one line to /etc/fstab for every new partition you just created on the new drive.

Your first drive should be hda. The second is hdb. Assuming you formatted the drive with the ext3 filesystem, you'd need some lines like this:

```

/dev/hdb1       /media/firstmountpoint       ext3    defaults        0       2
/dev/hdb2       /media/secondmountpoint      ext3    defaults        0       2

```

As jimrz says above, you need to create the mount points on the first drive. These are just part of the directory structure that will point to the second drive when they get mounted. So in my example above, you'd need to create firstmountpoint and secondmountpoint.

---

### Post by gantww on 2006-04-25
Awesome.
Thanks to everyone for all the help. The quality of responses in these forums is incredible. I'm several steps closer to escaping windows.

Thank you

---

