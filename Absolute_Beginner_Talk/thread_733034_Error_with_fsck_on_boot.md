---
title: "Error with fsck on boot"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-03-23
Each time I boot the computer, it tells me something about fsck and asks me something about root password (or to press ctrl-D to continue). If I press ctrl-D, then it continues to boot normally, but if I put root password it logs me into a shell and tells me to see a log file, that contains:

```

Log of fsck -C -R -A -a 
Sun Mar 23 12:12:15 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=11f622da-749f-4596-9e43-8f9216d7a0cc'

fsck died with exit status 8

Sun Mar 23 12:12:15 2008
----------------

```

Any help on this?

---

### Post by tgilber1 on 2008-03-23
it looks like your OS is configured to mount using the UUID of the hard disks and the UUID is invalid.  

You can configure the OS to mount the disk using LABEL, UUID, or directly via the device entry

Try using the the device instead by editing your /etc/fstab file.

ex.
# Entry for /dev/sda1 :
#LABEL=/boot /boot ext3 defaults 0 2
/dev/sda1 /boot ext3 defaults 0 2
#UUID=41b5f2b5-1eb5-4436-9511-62faf14f0501 /boot ext3 defaults 0 2


Notice the line that starts with the absolute path of the device - /dev/sda1.  You must populate your settings in lieu of the example above.

e.g., /dev/hdxy or /dev/sdxy with x= to the partition letter and y=to the partition#

/dev/sda1, /dev/hda2, etc.

After updating the /etc/fstab, issue the following command to automatically mount the partitions in the fstab file to ensure there are no errors.

If there are not any errors, then reboot.

---

