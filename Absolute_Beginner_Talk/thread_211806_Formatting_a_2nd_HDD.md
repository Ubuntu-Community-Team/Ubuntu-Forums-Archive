---
title: "Formatting a 2nd HDD"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2006-07-08
I have Ubuntu installed on the primary HDD and have installed a 2nd HDD which is formatted NTFS.  I want to format this new drive for Extended 3 and use it for a file drive only.

I tried running the FDISK command on the Konsole and must be doing something wrong.  Also, I am not sure why this 2nd disk is coming up under /tmp instead of /etc or somewhere else.

> Unable to read /tmp/disks-conf-hdb1
jason@esau:/tmp/disks-conf-hdb1$ fdisk -l /tmp/disks-conf-hdb1
jason@esau:/tmp/disks-conf-hdb1$ fdisk -l
jason@esau:/tmp/disks-conf-hdb1$ fdisk --help
fdisk: invalid option -- -

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


I don't really want to keep the NTFS partition, this is a totally blank drive right now.  I just want to partition it and format it for Linux.  Is there a GUI tool in Ubuntu?  Or should I be using the Konsole?

---

### Post by John.Michael.Kane on 2006-07-08
You should be able to format the drive using gparted.
```
sudo aptitude install gparted
``` theres also a [**[COLOR="DarkRed"]gparted live cd[/COLOR]**]("http://gparted.sourceforge.net/livecd.php").

---

### Post by kc5hwb on 2006-07-09
And Gparted is a GUI application?  I am running the install now.

---

### Post by sewmyheadon on 2006-07-09
> **kc5hwb said:**
> And Gparted is a GUI application?  I am running the install now.

Yes, you've probably already seen by now that Gparted is the Gnome partition editor.  A GUI version of 'parted' from the command line.

---

### Post by kc5hwb on 2006-07-09
> **sewmyheadon said:**
> Yes, you've probably already seen by now that Gparted is the Gnome partition editor.  A GUI version of 'parted' from the command line.


Thank you, that worked perfectly.  Except that after I formatted this 2nd HDD, I am still getting the same error when trying to mount it.  It says that it cannot mount the volume because it isn't removeable.

I am going to Places -> Computer -> and double-clicking on this drive.  I also try to right-click from this window and get the same error.

---

### Post by kc5hwb on 2006-07-09
Something new I just discovered....when I go to System -> Administration -> Disks and choose my 2nd HDD, it doesn't show a Path on the Partition tab.  When I drill down to /dev the "hdb1" is grayed out so I can't access it.  What should this be?

---

### Post by kc5hwb on 2006-07-09
Any ideas here?

---

### Post by kc5hwb on 2006-07-10
Still wondering about this one...

---

### Post by John.Michael.Kane on 2006-07-10
gparted or what ever method you used should have allowed  you the option to name the partition ect..

---

### Post by kc5hwb on 2006-07-13
It did let me rename it.  But it didn't let me choose the path.

---

### Post by moshuptrail on 2006-07-13
On my system, Ubuntu mounted my spare partition as /media/hda1
The partition I gave it for home was mounted as /home
and the root partition was mounted as /

I'd look under /media and see if it put your disk there.

---

