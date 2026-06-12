---
title: "cannot mount secondary master hard disk"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by germel_021404 on 2007-11-20
i have all my important files in my secondary master hard disk, but when i try to open it an error appear that says "UNABLE TO MOUNT THE SELECTED VOLUME" What should i do, i really need the files in the hard disk.

---

### Post by banewman on 2007-11-20
What is the command you are using to mount the disk?
 Should be      sudo mount /dev/sdb        or something similar. :)

---

### Post by germel_021404 on 2007-11-20
i'm really new to ubuntu, i just tried to open it in the computers but the error appear. when i click details it says that "error: device /dev/hdc4 is not removable

error: could not execute pmount" what should i do. i really need help.

---

### Post by logos34 on 2007-11-20
In a terminal run the commands

**sudu fdisk -l**

and 
[B]
cat /etc/fstab [/B]

and post the output.  Is this an ntfs volume?

---

### Post by mdpalow on 2007-11-20
usually you would enter something like this in a terminal window:

sudo mount /dev/sdb1 /media/some_name_here

<where "some_name_here" is the name you want to give the drive/mount>

However, we don't know how you have your hard drives partitioned and being used, so it might NOT be 'sdb1,' but something else.

Can you do a:

sudo fdisk -l    (in your terminal window)

and post the output here for us to see?

If we can get it mounted, then we can update your '/etc/fstab' file updated, so it automatically mounts the drive when you boot up...

Will await your answer...

---

### Post by germel_021404 on 2007-11-20
it has an edubuntu OS but not working, we need the files in the disk thats why we tried put it to secondary in order to back up the files. what will i do?

---

### Post by germel_021404 on 2007-11-20
how will we post it? im really new here so please bear with me guys. Thanks

---

### Post by mdpalow on 2007-11-20
highlight output with your mouse and COPY. Then past to this thread.

---

### Post by germel_021404 on 2007-11-20
Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         122      979933+  83  Linux
/dev/hdc2            9451        9729     2241067+   5  Extended
/dev/hdc3   *         123         366     1959930   83  Linux
/dev/hdc4             367        9450    72967230   83  Linux
/dev/hdc5            9637        9729      746991   82  Linux swap / Solaris
/dev/hdc6            9544        9636      746959+  82  Linux swap / Solaris
/dev/hdc7            9451        9543      746959+  82  Linux swap / Solaris

---

### Post by banewman on 2007-11-20
OK we'll go one step at a time. :)
You need to go to your menu  applications(at the top) - then accessories - then click terminal  - a window opens that lets you enter commands to control the computer.
You need to type - 
sudo mkdir /media/edubuntu
sudo mount /dev/hdc4 /media/edubuntu
(from what you've said this is the device that you can't mount).
Come back here and we'll go to the next step or try again :)

---

### Post by mdpalow on 2007-11-20
this is not all of the output... are you saying this (hdc) is the drive for sure?

---

### Post by germel_021404 on 2007-11-20
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         122      979933+  83  Linux
/dev/hdc2            9451        9729     2241067+   5  Extended
/dev/hdc3   *         123         366     1959930   83  Linux
/dev/hdc4             367        9450    72967230   83  Linux
/dev/hdc5            9637        9729      746991   82  Linux swap / Solaris
/dev/hdc6            9544        9636      746959+  82  Linux swap / Solaris
/dev/hdc7            9451        9543      746959+  82  Linux swap / Solaris

---

### Post by germel_021404 on 2007-11-20
thans benewman it work. is there a way to recover my files? it did mount but my files were missing.

---

### Post by banewman on 2007-11-20
Is the file completely empty?

---

### Post by germel_021404 on 2007-11-20
yup. could i still recover my files?

---

### Post by mdpalow on 2007-11-20
I would have said the same thing as 'banewman'

In your terminal type:

sudo mkdir /media/edubuntu
sudo mount /dev/hdc4 /media/edubuntu


I'm not sure why the drive is coming up as hdc... I would have expected something like sdc. I've typically seen hd. usually referring to a cd-rom or something. Anyone able to weigh in on that???

However, the SUDO commands above are how you usually mount a drive, so give that a try.

Then click on the drive and see if it works.

If it works, I would consider getting all your data off it and then maybe re-doing that drive and trying to get it down to one partition with an 'sdb1' partition name. Let's see if it mounts first though... and then proceed..

---

### Post by banewman on 2007-11-20
We need to check that it did mount - 
in a terminal type - 
sudo umount -v /dev/hdc4
(the -v is for verbose and will tell if it wasn't mounted)

---

### Post by mdpalow on 2007-11-20
banewman... you're in on this thread too, so I'm going to bed now. Good luck.

---

### Post by germel_021404 on 2007-11-20
all i see were files of edubuntu, the folder home is empty. could i still recover the files?

---

### Post by vinutux on 2007-11-20
> **mdpalow said:**
> I would have said the same thing as 'banewman'

In your terminal type:

sudo mkdir /media/edubuntu
sudo mount /dev/hdc4 /media/edubuntu


I'm not sure why the drive is coming up as hdc... I would have expected something like sdc. I've typically seen hd. usually referring to a cd-rom or something. Anyone able to weigh in on that???

However, the SUDO commands above are how you usually mount a drive, so give that a try.

Then click on the drive and see if it works.

If it works, I would consider getting all your data off it and then maybe re-doing that drive and trying to get it down to one partition with an 'sdb1' partition name. Let's see if it mounts first though... and then proceed..



Sdc stands for SATA hard disk if u r disk is non -sata it is called hda or hdc etc :guitar:

---

### Post by banewman on 2007-11-20
One of the files in the edubuntu files is home.
Browse through and you will see it.
Let us know if you find it please. :)

---

### Post by vinutux on 2007-11-20
If u mount harddisk in /media/edubuntu go there with nautilus to see all of ur files not in home folder .If your files are hidden press ctrl+h

---

### Post by banewman on 2007-11-20
Apologies.
If that home folder is empty then there are no files or they are somewhere else on the disk or they are on another disk.... can't help more than that. :)

---

