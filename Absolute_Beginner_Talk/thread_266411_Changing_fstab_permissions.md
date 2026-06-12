---
title: "Changing fstab permissions?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by bocmaxima on 2006-09-27
Hi, I seem to need to give "read" access to my CD drive as well as "read" and "execute" access to my mount point. I am not sure how to go about this.

It looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

What do I change?

---

### Post by bodhi.zazen on 2006-09-27
You do not need to edit fstab.

To burn use k3b.

To use as a read-write drive see here:

[[color=blue]CD-RW[/color]](http://ubuntuforums.org/showthread.php?t=129093)

---

### Post by bocmaxima on 2006-09-27
I am trying to get the copy protection support working in Cedega. It says
> Many Windows games use copy protection systems that require Cedega to have 'read' access to your CD/DVD device, as well as 'read' and 'execute' access to your CD/DVD mount point. Check your CD/DVD devices and mount points to ensure that Cedega has appropriate permissions. Some forms of copy protection require the ability to see hidden files on the disc. To make these files available to Cedega, you will also need to add the "unhide" option to the CD/DVD fstab list. (In particular, SuSE 9.3 users should note that the unhide option is incompatible with the subfs auto mounting solution provided with this distribution. SuSE 10 and later do not share this drawback.) You will need root permissions to make changes to your /etc/fstab.

To ensure that the correct permissions are available:

Check the /etc/fstab file for the line that represents your CD/DVD drive. That line should indicate the device such as /dev/hdc or /dev/scd0.

For example:

/dev/cdroms/cdrom0 /mnt/cdrom iso9660 user,unhide,noauto,ro 0 0

In the above example the device is /dev/cdroms/cdrom0

Perform ls -la /dev/DEVICE on the CD/DVD device. Check to see if all users have rx permissions. The example below does not have the correct permissions:

brw------- 1 wulfram disk 22, 0 Aug 26 06:20 /dev/hdc

Your permissions should look like:

brwxr-xr-x 1 wulfram disk 22, 0 Aug 26 06:20 /dev/hdc

(you may also have W permissions, but they are not necessary for Cedega to run).

To change the permissions on your device and mount points, execute the following commands as 'root':

# chmod a+xr [device]

# chmod a+rx [mount point]

In some cases the device may be a symbolic link to another device (indicated by -> /cdroms/cdrom0 for example) If this is a symbolic link, you will also need to check the permissions on the linked device.

For example:

lr-xr-xr-x 1 root root 13 Aug 21 14:45 /dev/cdrom -> cdroms/cdrom0

In this case, you would check the permissions of /dev/cdroms/cdrom0 as well.

I tried everything but the Symbolic Link. How would I know if it was a symbolic link?

---

### Post by bodhi.zazen on 2006-09-27
Not sure where you are exactly as it was a long post....

Can you post the output of these two commands:```
ls -la /dev
ls -la /mnt
```
As far asyour question:

Do you see the small "L" in this output?

[color=red]**l[/color]**r-xr-xr-x 1 root root 13 Aug 21 14:45 /dev/cdrom -> cdroms/cdrom0

That smalll "L" means it is a link.

---

