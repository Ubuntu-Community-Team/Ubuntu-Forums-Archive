---
title: "Noob: Permissions problem with mounting Windows in Edgy 64"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by tkeseth on 2006-12-12
Hi all.  I followed one of the readily available guides on mounting XP to my hard drive.  When I now go to the mounted folder (/windows), I get the following error:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "windows"."

My fdisk -l looks like this:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8025    64460781    7  HPFS/NTFS
/dev/hda2            8026        9655    13092975   83  Linux
/dev/hda3            9656        9729      594405    5  Extended
/dev/hda5            9656        9729      594373+  82  Linux swap / Solaris

And, my fstab looks like this:

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=ec5ecfb7-ec53-418a-8eb1-89fb621422fe /               ext3    defaults,erro$
# /dev/hda5
UUID=03435a77-5d67-4220-bcb9-bc8205938be1 none            swap    sw           $
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1  /windows  ntfs  defaults  0  0

I'm pretty sure that the problem lies somewhere in the fstab, but I'm too much of a noob to figure out exactly where it is.

Any help, please?

---

### Post by xyz on 2006-12-12
Try this. It's excellent:
[ Mounting Windows Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountwindows")
I don't how new you are to all this but, in case you encounter pbms, don't hesitate to come back here to ask clarifying questions.
Good luck though!

---

### Post by tkeseth on 2006-12-12
Right off the bat I get an error in the terminal saying that sudo unmount /windows is a bad command:

sudo: unmount: command not found

...to be specific.  Sorry about the trouble.  I'm a noob (1st day on Linux), but I learn fast!

Thanks,

---

### Post by deadgobby on 2006-12-12
Have you check this yet?
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by xyz on 2006-12-12
Hi,
Well right off the bat, too, is this what you ran:
```
sudo unmount 
```
Unless it's a typo, the command line is:
```
sudo umount /media/hda1
```
Hopefully it's that simple!!

---

### Post by DerHesse on 2006-12-12
Regarding your actual question. I had the same problem.
**Instead of:**
/dev/hda1 /windows ntfs defaults 0 0
**try:**
/dev/hda1 /windows ntfs dmask=000,uid=1000,gid=1000,rw,user,auto    0       0

---

### Post by DerHesse on 2006-12-12
> **DerHesse said:**
> Regarding your actual question. I had the same problem.
**Instead of:**
/dev/hda1 /windows ntfs defaults 0 0
**try:**
/dev/hda1 /windows ntfs dmask=000,uid=1000,gid=1000,rw,user,auto    0       0

I am not sure about your uid and gid. Check your uid and gid by typing at the prompt: $ tail /etc/passwd

(**1000:1000** is user the account created during installation)

---

### Post by tkeseth on 2006-12-13
DerHesse, xyz, thank you both very much.  That little 'sudo unmount' thing was holding me back.  I edited my /etc/fstab file according to DerHesse's instructions (and the 'tail /etc/passwd' file), then remounted the image to /windows and BAM! it worked!

Thanks again,

---

