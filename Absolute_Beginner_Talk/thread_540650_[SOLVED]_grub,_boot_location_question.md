---
title: "[SOLVED] grub, boot location question"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Dainn on 2007-09-01
I am attempting to install XP using the following directions: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) 
It appears that my boot partition is not hd0,0, which is causing problems with the XP installation.  It seems that my boot partition is hd0,4.  

How do I work with this?

Is there a way to continue the XP installation and tell it to point to this location?
Is there a way to change it to hd0,0?

If I'm not looking at this the right way, or there is something else I am missing, please let me know.

Thanks for your time - Dainn

---

### Post by southernman on 2007-09-01
The thing (ok ONE of them) is you can't tell MS where to install the boot loader... it goes to the MBR (hd0,0) by default with no way to change it... AFAIK at least.

What you'll have to do is continue with the installation and let Windows have it's way, then reinstall grub.

---

### Post by Dainn on 2007-09-01
Thanks southernman.  I have no problem with that, it's just that the installation is not moving from beyond that point.  I'm going to try it again, and see if I notice something I didn't before.

Thanks again.

---

### Post by louieb on 2007-09-01
I just looked at that article. I'd be confused to. Two much better places to get Dual boot tutorials are [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") and [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") 

It would easier to help if you could post a screen shot of the GParted window. 
southernman's  sugestion is a good a way as any just let windows have it way and clean up the mess later.

---

### Post by alienexplorers on 2007-09-01
please list your sudo fdisk -l and /etc/fstab files and post them here.

---

### Post by southernman on 2007-09-01
> **louieb said:**
> It would easier to help if you could post a screen shot of the GParted window. 
I'm with louieb on this as well. Could you boot with a livecd and take a screenshot of gparted showing your disk layout... and post that screeny as an attachment here?

Or you could do as alienexplorers suggest and post the output of "sudo fdisk -lsu"

---

### Post by Dainn on 2007-09-02
ok, sorry about the long wait.  Thanks for the replies. 

Here is a screen shot of gparted:

[http://s216.photobucket.com/albums/cc288/eiramnnaid/?action=view&current=Screenshot-1.png](http://s216.photobucket.com/albums/cc288/eiramnnaid/?action=view&current=Screenshot-1.png)


When I started on this, the hdc5 and the unallocated area's where flip-flopped.

Here is the fdisk:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1652    13221495    5  Extended
/dev/sda3            1653        3648    16032870   83  Linux
/dev/sda5   *         765        1566     6442065   83  Linux
/dev/sda6            1567        1652      690763+  82  Linux swap / Solaris

Disk /dev/sdb: 1994 MB, 1994292736 bytes
4 heads, 16 sectors/track, 60860 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60861     1947543+   e  W95 FAT16 (LBA)

The error I keep looping with in the XP install is along the lines of, there is no XP compatable drive, please go back to the previous screen and create one.
When I go back to the prev. screen and create a partition, it still tells me the same error.  I go back, delete the partition, and the loop starts again. -- I have also tried making the unallocated area into NTSF in gparted, but this didn't help either

Once again, Thank you for your help - dainn

---

### Post by meierfra on 2007-09-02
Windows needs to be installed on a primary partition (that is a partition which is not inside an extended partition). So you need the shrink the extended partition. This will give you some unallocated space outside the extended partition, which you can use to install windows.

---

### Post by Dainn on 2007-09-02
ahh, ok.  I will try to do that.  Thanks meierfra

---

