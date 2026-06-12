---
title: "two probs"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-29
1 how can i see my fat32 partition and move files back and forth???

2 is there a program that will batch rename my image files???


thanks in advance!

---

### Post by meng on 2006-12-29
You should be able to mount the partition, e.g.
sudo mount -t vfat /dev/hda5 /media/hda5
How do you want to rename the files? It can be done fairly easily with a terminal command (or one-line shell script).

---

### Post by ComplexNumber on 2006-12-29
1) do you mean your windows partition?
2) krename

---

### Post by antgul3382 on 2006-12-29
no windows just a empty fat32 partition


so i can batch rename 10,000 images in the terminal???  how do i do that?

---

### Post by meng on 2006-12-29
Give me an example of how you want to rename? e.g. upper case to lower case?

---

### Post by antgul3382 on 2006-12-29
> You should be able to mount the partition, e.g.
sudo mount -t vfat /dev/hda5 /media/hda5

did that got this

> mount: mount point /media/hda5 does not exist




2  i want them renamed from 00001.jpeg - 10000.jpeg

---

### Post by meng on 2006-12-29
e.g. means for example, it doesn't mean "quick do this immediately" :p

I have no idea where your fat partition is! It may not be located on /dev/hda5
Also /media/hda5 was an example of a mountpoint. It has to exist before you can mount anything to it.

I gather you're new, which is great, but take things slowly, read posts carefully and above all describe exactly what you want to do, and what you've already tried (which didn't work). Yes, it takes you longer to write the first post, but it minimizes the back-and-forth that follows, and ultimately gets you a solution more quickly.

Now DO THIS:
sudo fdisk -l
(and enter your user password, obviously you already know you have to do that)

and tell us what the result is.

EDIT:
Also, DO THIS:
cat /etc/fstab

and post the result here.

---

### Post by antgul3382 on 2006-12-29
> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12378    99421528+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       12379       19166    54524610   83  Linux
/dev/hda3           19167       19457     2337457+   5  Extended
/dev/hda5           19167       19457     2337426   82  Linux swap / Solaris
slave@slave3:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=27581109-0db4-48a5-9b55-e2b582ba43cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0f2a8ad7-65ac-416a-b976-d6ef5b4378f7 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0


thanks for the help1

---

### Post by meng on 2006-12-29
Ok try this:
sudo mkdir /media/hda1
(you only need to do this once, it will create a permanent directory/mountpoint in your filesystem)

Next:
sudo mount -t vfat /dev/hda1 /media/hda1

Now if you navigate to /media/hda1 you should be able to at least browse this partition.
There should probably be an icon on your desktop or a place/bookmark in your file browser once the partition is mounted.

To unmount:
sudo umount /media/hda1

Play around with it, see if you have permissions to alter files, then report back and we can discuss how to have this partition mount automatically in future.

And now some general advice:
Be patient! Be courteous! Post problems in detail! Search these forums or the web at large! Don't expect Ubuntu/Linux to be like Windows! Recognize that 64-bit installations are much trickier for the beginner than 32-bit installations (also recall that 64-bit Windows doesn't work very well at all)!

And if your frustrations get too much for you and you have to give up, don't take it so bad, perhaps you'll come back for another try someday.

---

### Post by antgul3382 on 2006-12-29
ok i went into nautilus and make that directory hda1 under media -.> the typed that command to mount the paRtition - > it was empty like it supposed to be, so i cut and pasted my audio, video, and image folders -> it said i had no permissions -> went back to nautilus and cut and paste them now its moving them.... so it worked?!?   now will this be visible all the time??? like the next time i reboot?? and how can i make a shortcut of this to my dektop???

---

### Post by meng on 2006-12-29
Add the following line to your /etc/fstab:
/dev/hda1    /media/hda1  vfat    iocharset=utf8,umask=000   0   0

(the number of spaces between items is unimportant)

In order to edit your /etc/fstab, I recommend you use gedit (gnome text editor) and you'll have to run it with superuser privileges (since it's a system configuration file, ordinary users don't have the right to screw it up):

drop to terminal (or alternatively, just press alt-f2 to run a single-line command):
gksu gedit /etc/fstab

(add the line)
Now it should automatically mount at boot time.

---

### Post by antgul3382 on 2006-12-29
yeah i rebotted after moving from ubuntu folders to my fat32 partition and i have the folder but no file    wtf did id wrong please get back to me


thanks

---

### Post by antgul3382 on 2006-12-29
> Add the following line to your /etc/fstab:
/dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0

(the number of spaces between items is unimportant)

In order to edit your /etc/fstab, I recommend you use gedit (gnome text editor) and you'll have to run it with superuser privileges (since it's a system configuration file, ordinary users don't have the right to screw it up):

drop to terminal (or alternatively, just press alt-f2 to run a single-line command):
gksu gedit /etc/fstab

(add the line)
Now it should automatically mount at boot time.


ok i got gedit up here so i just copy and paste that line on the bottom???

---

### Post by bulldog on 2006-12-29
> **antgul3382 said:**
> ok i went into nautilus and make that directory hda1 under media -.> the typed that command to mount the paRtition - > it was empty like it supposed to be, so i cut and pasted my audio, video, and image folders -> it said i had no permissions -> went back to nautilus and cut and paste them now its moving them.... so it worked?!?   now will this be visible all the time??? like the next time i reboot?? and how can i make a shortcut of this to my dektop???

Take your time and explain the cutting and pasting.

If you mount a partition,you can see the partition in the created mount point.
From there,you have to navigate to the folder of course, you can access,if you have the rights ,your files **without the cutting and pasting**
If not,you made probably a mistake with either the mount point or the mounting itself.

---

### Post by antgul3382 on 2006-12-29
ok i got it iup there alls well

except for the permissions, i have to use nautilus everytime i wanna do anything how can i change this???

---

