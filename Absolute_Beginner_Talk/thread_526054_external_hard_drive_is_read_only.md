---
title: "external hard drive is read only"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Ryn9190 on 2007-08-15
Hi I'm very new to Ubuntu and to Linux so i apologize in advance for being a total moron about this stuff

I'm trying to use a hard drive that I had been using in windows but it keeps mounting it as read only and I have no idea where the option to change that is

I know there are other posts with this problem and I've read them all and tried to do what they say but I either don't understand it or it doesn't change anything

basically how do i get the thing to mount as read and write?

Its a maxtor and the mount options are:
ro nosuid nodev fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8
(i assume the ro means read only but i don't know how to change it)

sorry i don't really know what information would be useful to put up

---

### Post by Jimmyfj on 2007-08-15
You would want to install NTFS Read/Write support for the disk. You can do that either from Programs>Add/Remove>System tools or Synaptic

---

### Post by Ryn9190 on 2007-08-15
The file system is vfat though

(sorry definitely should have said that)

---

### Post by overdrank on 2007-08-15
HI I would believe that would be 
```
ntfs-3g & ntfs-config
```

Edit: did not see the vfat comment but this thread was discussed this day
[http://ubuntuforums.org/showthread.php?t=525732&highlight=vfat+read+write](http://ubuntuforums.org/showthread.php?t=525732&highlight=vfat+read+write)

---

### Post by mattmole on 2007-08-15
Hi.

Information about mounting (permanent) harddrives are stored in /etc/fstab. Unfortunately, removable media is not listed here.

Personally I would try the following:

sudo chmod a+rw /WHERE/THE/DRIVE/MOUNTS

The above line will change the ownership of the directory where the drive is mounted. It will make it read and writable by all.

Hope that helps!

Mattmole

---

### Post by Ryn9190 on 2007-08-15
that just gives me

chmod: changing permissions of `/media/FRANK': Read-only file system

(I have no idea who named the drive FRANK or why but I dont know how to change that either lol)

---

### Post by ravendiana on 2007-08-15
there are several fixes here [http://lists.netisland.net/archives/plug/plug-2006-09/msg00057.html](http://lists.netisland.net/archives/plug/plug-2006-09/msg00057.html) includeing quite a few that seem to be geared for your file type.  I JUST fixed this problem, but mine was ntfs

---

### Post by mattmole on 2007-08-15
Hi Ryan9120,

When you ran the command did you issue "sudo" before "chmod ...".

Are you manually mounting the drive or letting Ubuntu do it for you? How did you generate the list of mount options you posted earlier?

Mattmole

---

### Post by Ryn9190 on 2007-08-15
When you ran the command did you issue "sudo" before "chmod ...".

Yes

Are you manually mounting the drive or letting Ubuntu do it for you? 

Ubuntu does it automatically

How did you generate the list of mount options you posted earlier?

It comes up as an icon on the desktop, I went to properties and then volume and it was listed there

---

### Post by Ryn9190 on 2007-08-27
Bump

---

### Post by olavjunior on 2007-08-29
I have the exact same problem Annoying, cannot empty the trash on my external drive. I only get this problem now and then

---

### Post by jw5801 on 2007-08-29
First run ```
mount | grep /media/FRANK
```so you can see where the device is registered (should be /dev/sdb1 or similar). Then unmount it and try manually mounting it with read write permissions from the command line: ```
sudo umount /media/FRANK
sudo mkdir /whereever_you_want #you need to have created the directory you want to mount to
sudo mount -t vfat -o rw /dev/*results_of_above* /whereever_you_want
```
If that works then add it to your fstab with ```
sudo -s
echo "/dev/*results_of_above*  /whereever_you_want  vfat  rw,user,auto 0 0" >> /etc/fstab
exit
```
which should let any user automatically mount the drive when you connect it.

EDIT: Or... if you right click on the drive on your desktop while it's mounted, go to the "Volume" tab and under where it says mount options there should be a menu you can expand named settings, copy the mountpoint and filesystem from the bits above and also copy the mount options but change the "ro" to "rw". That's a little bit easier for a new user... although if you want to learn about the command-line, feel free to try my first method, and ask about any of the commands if you're unsure what they do! :p

---

### Post by olavjunior on 2007-08-29
I think my problem is an error on my drive actually. Some FOUND-folder I cannot delete. When I try to delete it, it gets write-protected. It's no big deal though...

---

### Post by jw5801 on 2007-08-29
> **olavjunior said:**
> I think my problem is an error on my drive actually. Some FOUND-folder I cannot delete. When I try to delete it, it gets write-protected. It's no big deal though...

If your drive is formatted as ext3 then you'll have a lost+found folder which you shouldn't delete. Otherwise if it's a permissions error then you can use```
sudo rm -r /directory
```to kill it. If it's just your drive being cranky then there's not much we can do about it.

---

### Post by Yizi on 2007-08-29
> **jw5801 said:**
> First run ```
mount | grep /media/FRANK
```so you can see where the device is registered (should be /dev/sdb1 or similar). Then unmount it and try manually mounting it with read write permissions from the command line: ```
sudo umount /media/FRANK
sudo mkdir /whereever_you_want #you need to have created the directory you want to mount to
sudo mount -t vfat -o rw /dev/*results_of_above* /whereever_you_want
```
If that works then add it to your fstab with ```
sudo -s
echo "/dev/*results_of_above*  /whereever_you_want  vfat  rw,user,auto 0 0" >> /etc/fstab
exit
```
which should let any user automatically mount the drive when you connect it.

EDIT: Or... if you right click on the drive on your desktop while it's mounted, go to the "Volume" tab and under where it says mount options there should be a menu you can expand named settings, copy the mountpoint and filesystem from the bits above and also copy the mount options but change the "ro" to "rw". That's a little bit easier for a new user... although if you want to learn about the command-line, feel free to try my first method, and ask about any of the commands if you're unsure what they do! :p

This worked for me, thanks a lot :KS

---

### Post by olavjunior on 2007-08-30
> **jw5801 said:**
> If your drive is formatted as ext3 then you'll have a lost+found folder which you shouldn't delete. Otherwise if it's a permissions error then you can use```
sudo rm -r /directory
```to kill it. If it's just your drive being cranky then there's not much we can do about it.

It gave me a long list of write-access errors: 
> rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9983.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9984.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9985.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9986.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9987.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9988.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9989.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9990.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9991.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9992.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9993.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9994.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9995.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9996.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9997.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9998.CHK»: Read-only file system
rm: cannot remove «//media/LACIE_/.Trash-junior/FOUND.000/FILE9999.CHK»: Read-only file system


---

### Post by jw5801 on 2007-08-30
Hmm... what's the output of: ```
mount | grep /media/LACIE_
``` Your output means that it's not a permissions error, but it's quite likely that your drive is mounted as read only.

---

### Post by JamesD-severnapark on 2007-09-03
echo "/dev/results_of_above  /whereever_you_want  vfat  rw,user,auto 0 0"


That's the line I needed.    Thanks!

---

