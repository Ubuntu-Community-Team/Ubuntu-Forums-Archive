---
title: "ran out of disk space"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by murmsk on 2006-12-08
I ran out of disk space when downloading and now the system won't boot.

I booted off of a CD and mounted the HD but can't delete or copy because I don't have permission. I can't change permissions eather because the HD doen't recognise me.

any ideas

thanks  steve

---

### Post by bulldog on 2006-12-08
If you want to delete something in the /home folder,use the sudo command.
```
sudo rm what ever you want
```
You have to go to the /home folder first of course.

If you can mount your ubuntu sudo works.

---

### Post by SyvanX on 2006-12-08
I had this problem once on a different distro, with a strange partitioning scheme.  

Boot up the live cd, then open a Terminal.

enter the following command to get a root shell:

```
sudo -s
```

If you feel comfortable with the text interface, you can go from here and remove the file you downloaded.  Otherwise you can start a filemanager with one of the following commands depending on whether you are using Gnome or KDE.

Gnome:
```
nautilus
```

KDE:
```
konqueror
```

From here you can use the normal file-manager to manage your hard drive.

---

### Post by murmsk on 2006-12-08
I still get a permission error after using the sudo -s. I deleted or should I say moved to the trash but it didn't open any space on my HD. do I have to empty the trash?  where is the trash for the HD.

thanks  steve

---

### Post by SyvanX on 2006-12-08
That's odd the permissions aren't right with root access.  I have a couple follow-up questions.

[LIST=1]
[*]Is the partition with no extra space formatted ext3 (Ubuntu)?

[*]What is the specific error you are getting when you try to get root access?

[*]How did you move the files to the trash? (Command line or GUI)

[/LIST]

---

### Post by murmsk on 2006-12-08
1. the partition is ext3
2.you don't have permission to read this file or something like that

3. I used nautilus to find the files then highlighted them and "moved to trash"

thanks  steve

---

### Post by SyvanX on 2006-12-08
I have an idea.  Maybe you've already checked this.
Boot into your livecd again, but look at your fstab file

```
nano /etc/fstab
```

in the line where the filesystem type is ext3, look at the options in the next column.  It should look like this, my options are 

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    **defaults,errors=remount-ro** 0       1
/dev/hda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I'm guessing one of your options for that drive is "ro" or Read Only.  If that's your problem, change that option to "defaults,rw" then run:

```
sudo umount /dev/hda1 # change /dev/hda1 to your device name from the first column of fstab
sudo mount /dev/hda1 # use the same device from above.
```

---

