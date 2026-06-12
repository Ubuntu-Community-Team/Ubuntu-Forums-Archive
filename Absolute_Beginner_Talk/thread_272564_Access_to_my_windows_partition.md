---
title: "Access to my windows partition"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Stephen Shellard on 2006-10-06
I have just installed ubuntu on my recently purchased system which came installed with Windows XP home addition. I partitioned the hard 80GB hard disc with 20GB for Ubuntu. (Meant to do it the other way round, but misread the slider which set the partition; I am told however that 20GB is likely to give me plenty of space for Ubuntu). I have networked this system with an existing computer running windows XP professional and can read the other computer's files across the network; however I am still unable to read the windows side of the partition when logged onto ubuntu.  With some excellent help from a colleague at work (I mention this as some of what follows may suggest greater knowledge than I actually have) I have mounted the disk using a two stage process in a terminal window:  sudo mkdir /media windows  followed by: sudo mount/dev/hda1 /media/windows/ -tntfs -o nls=utf8,umask=0222

Following this I can see the root of the windows partition when I clickon Places/computer  under the name p4800-M7_HOME  However when I click on the drive it returns the message: You do not have the permission to view the contents of disks-conf-hda1  Basic information in properties suggest the file is unreadable though its size is given as 58.2GB.  In disks manager the partition properties are given as Device /dev/hda1  Access path /tmp/disks-conf-hda1  Status Accessible   However, I am unable to access it.  Help greatly appreciated.

---

### Post by CatKiller on 2006-10-06
```
sudo umount /dev/hda1
``` should get rid of the drive from /tmp, and then the commands you've listed above should mount the drive in your sensible /media/windows, although I suspect you want a space between the t and the ntfs. You can edit your /etc/fstab to do this automatically on boot up. Search this forum - there are many posts outlining how to do this.

Welcome to the forum.

---

### Post by Stephen Shellard on 2006-10-07
Thank you.  That has worked just fine. I was a little puzzled initially as you speak of *getting rid of* the drive from tmp and after I had run the command I looked to see what its effect was and it - the drive -  was still there (or so it seemed to me) as large as life; however, I had faith, and ran the other command (you were of course correct in spotting the missing space between t and ntfs.) Pleased to report it all works fine now.  

I have been warned of etiting the fstab file, there being a potential, I believe to do much damage if it goes wrong,  so I suppose I shall mount the drive manually as required in the meantime, though I shall reconsider this once I have sorted out a few other things.  Thanks again.

---

### Post by CatKiller on 2006-10-07
It's just a text file. Provided you don't change any of the other lines, and just put in the new one that you want, then you'll be fine. [This page]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access") might help.

---

### Post by clarkth on 2006-10-07
> **CatKiller said:**
> It's just a text file. Provided you don't change any of the other lines, and just put in the new one that you want, then you'll be fine. [This page]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access") might help.

It should go without saying that you should make a backup of any file before changing it in case something does go wrong you can recover.

---

### Post by CatKiller on 2006-10-07
Good catch.

---

