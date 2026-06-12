---
title: "Windows Partition"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-06-05
Hey all! I'm trying to access my Windows partition from Dapper Ubuntu. 

I followed the instructions [here]("http://www.psychocats.net/ubuntu/mountwindows")
and all worked well. Its just that when I go to my /windows directory (created through that tutorial) everything is read only. Chmod 777 wont change the permissions either.

Here is the output of my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0**
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Thanks for the help!!!

---

### Post by jessecollins on 2006-06-05
Hopefully this can help.  Note that NTFS writing is still not completely fail proof.  

[http://ubuntuforums.org/showthread.php?t=142481]("http://ubuntuforums.org/showthread.php?t=142481")

---

