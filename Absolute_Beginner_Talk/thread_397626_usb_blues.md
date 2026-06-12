---
title: "usb blues"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by kelvin spratt on 2007-03-30
out of the blue my usb memory stick has stopped auto mounting and unmounting my card reader is working fine the error is Unable to mount the selected volume.        
mount: only root can mount /dev/sdb1 on /media/sdb1 can somebody explain how to get this working as i use it to transfer data i do not know the codes to use root but my reader says my name
as the owner and this says root as owner at the moment i'm using disc partitioner to mount but as soon as i try to use eject i get this
Unable to eject media
umount: only root can unmount /dev/sdb1 from /media/sdb1
eject: unmount of `/media/sdb1' failed    the flag is boot  i also can't write to it any more 
i'm getting faults on a daily basis at the moment so please try to helphttp://ubuntuforums.org/images/icons/icon5.gif

---

### Post by crispy_420 on 2007-03-30
Sounds like a permissions problem to me. Try mounting as root and change permissions so that all users have read/write/execute.

Did you format the drive? If so that may be the cause of this.

---

