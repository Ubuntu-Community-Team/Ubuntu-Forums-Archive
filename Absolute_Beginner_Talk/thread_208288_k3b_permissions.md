---
title: "k3b permissions"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-03
whenever i try to burn image using k3b it gives message that cdrecord do not have permission.

please tell me how to change the permission??:oops:

---

### Post by frodon on 2006-07-03
Do you have a fstab line to mount your cdrom ?

Adding a fstab line for my cdrom drive solved this issue for me.

---

### Post by wolfmaniac on 2006-07-03
please giv me details??

---

### Post by frodon on 2006-07-03
Post here your fstab file, use this command to open it : ```
sudo gedit /etc/fstab
```replace gedit by the editor of your choice
Then post here the output of this command line : ```
sudo fdisk -l
```Then i will tell you how to edit your fstab file.

---

### Post by wolfmaniac on 2006-07-03
sudo kate /etc/fstab 


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by wolfmaniac on 2006-07-03
wolfmaniac@zone:~$ sudo fdisk -l

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         956     7679038+  83  Linux
/dev/sda2             957        1912     7679070   83  Linux
/dev/sda3            1913        7296    43246980    5  Extended
/dev/sda5            1913        2001      714861   82  Linux swap / Solaris
/dev/sda6   *        2002        7296    42532056    b  W95 FAT32

---

### Post by frodon on 2006-07-03
I'll check that once at home but try to add the "rw" option in your fstab line, it would look like that : ```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,**rw** 0 0
```Then run a "sudo mount -a" to apply the changes.

---

### Post by wolfmaniac on 2006-07-03
rw ]0 0


is ] also there or typing mistake.

---

### Post by frodon on 2006-07-03
It's a mistake sorry, i edited my previous post to correct that.

---

### Post by wolfmaniac on 2006-07-03
did'nt worked

---

### Post by frodon on 2006-07-03
Here is the line which worked for me : ```
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
```If you still not able to find a solution try a "sudo chown -R your_username /media/cdrom0" and a "sudo chmod -R 777 /media/cdrom0" before puting a CD in the drive.
The k3b log may also help.

---

### Post by wolfmaniac on 2006-07-03
no success man.:( :confused: :( :confused:

---

### Post by wolfmaniac on 2006-07-03
i think i have to add a user in k3bsetup!!

how to do that?

---

### Post by wolfmaniac on 2006-07-03
got it!!!
locate:kcmshell last i burned my image
juzt opened it as root

kdesu k3b
and woila at last i burned the image

---

### Post by vincebs on 2006-07-04
Is there a way to run K3B as a normal user? That is, just clicking the k3b program?

I also did kdesu k3b, but this runs K3B as root. It works, but I would prefer to run it like any normal program.

---

### Post by romprod on 2006-07-26
> **vincebs said:**
> Is there a way to run K3B as a normal user? That is, just clicking the k3b program?

I also did kdesu k3b, but this runs K3B as root. It works, but I would prefer to run it like any normal program.

Can i also ditto this? k3b works fine either with sudo or as root, but it won't detect my dvd drive as a normal user. I assume i need to add that user to a certain group?

Russ

---

### Post by romprod on 2006-07-26
Ok, fixed this. Just go into the k3b setup and tell it what group you want to give access to. Simple really.... doh

---

### Post by linedpaper on 2006-11-15
I can't get into k3bsetup.  Every single time I go in there it asks for the root password, I type it in and then nothing happens.  No setup menu comes up or anything.  Anyone have this happen?

---

### Post by ThrobbingBrain66 on 2006-11-15
[quote=linedpaper]I can't get into k3bsetup. Every single time I go in there it asks for the root password, I type it in and then nothing happens. No setup menu comes up or anything. Anyone have this happen?[/quote]

I had something similar happen to me when was using Kubuntu.  The root cause is a bug with with scsi drives not being given the correct permissions.

this got rid of my burning issues

[http://www.ubuntuforums.org/showthread.php?t=217472&highlight=cd+burning+issues](http://www.ubuntuforums.org/showthread.php?t=217472&highlight=cd+burning+issues)

---

