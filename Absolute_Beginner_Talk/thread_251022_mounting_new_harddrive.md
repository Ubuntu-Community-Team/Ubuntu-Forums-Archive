---
title: "mounting new harddrive"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by RageAgainstThis on 2006-09-04
Ok i do not know if this is a hardware issue or not.  I have a 320 western digital harddrive in an old dell.  The dell is an xps 400 p2 400.  Well i fortmatted the drive in ext 3, since that is what ubuntu formatted the main drive as.  This drive will never be used outside of linux and i do not like fat32.  Anyhow i know when i a drive is formatted it loses storage.  So i am at approx 300 gb.  Then when i go to enable this drive, and i set the path for /mnt.  This works then i go to reboot and i have to set the path and enable again.  How would i correct this problem even though this comp will be used a storage server and will not be restarted too often.  

When i enable the drive i lose another 20 gb due to lost and found i believe.  Should and could i disable this?

---

### Post by dbasis on 2006-09-04
tryed to set up the harddisk in /etc/fstab?
you can get there by typing "sudo gedit /etc/fstab" into the terminal add an line for the new harddrive with its mountpoint (needn´t to be in "/mnt") all other settings u might copy from the already existing entry.

please let me know if it helped u

---

