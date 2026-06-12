---
title: "How do I uninstall Ubuntu and resize my NTFS  on my laptop?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-08-15
Hi,

Because of too much experimentation, my ubuntu partition on my tablet is hosed. Since school is coming up, I want to remove it from my hard drive and resize the NTFS partition back to full size.  Preferably, I'd like to do this without having to reinstall Windows. Anybody think they can help?

Thanks

P.S. I'm still using Ubuntu on my desktop. :p

---

### Post by coffeecat on 2006-08-16
If I was in your situation I would try the following. I'm assuming you want to end up with a single Windows partition occupying all of your hard disk. Boot up with the Dapper live CD. Once you have the Gnome desktop, open up Gparted (System > Administration > Gnome Partition Editor). You should see your NTFS Windows partition and the Ubuntu partitions. I say partiitions because there should be a swap one as well as the root Ubuntu one. Delete the Linux partitions. Now resize/enlarge the NTFS partition.

I can't guarantee that this will work because I've never tried it, but I believe that Gparted can resize NTFS partitions so it should work. However, do back up all you data and be prepared to reinstall Windows if something goes wrong. Partitioners do sometimes hang up or corrupt the partition table.

Another thing I personally would do is to make a ghost/image of my Windows installation with something like Acronis Disk Image or Norton Ghost. Then I would be able to restore Windows with all my apps and settings in one go. But this is proprietary software and you may not have it.

---

### Post by anaconda on 2006-08-16
Ang GRUB -boot manager wont work after you delete your ubuntu-partition! Because part of GRUB is in your /boot -folder..

So you have to boot with your windows CD and go to rescue and type "fixmbr" and "fixboot" (if I remember correctly..)
Or boot with a windows (95, 98, 2000 ) floppy and type "fdisk /mbr"

---

### Post by coffeecat on 2006-08-16
Thanks for chipping in with that, anaconda. I completely forgot about the MBR -  :oops: Too early in the morning. I need another cup of coffee. :wink:

---

### Post by anaconda on 2006-08-16
And if you dont have windows-CD,(like you said in your other post) then you can still repair your mbr, read:

[http://www.cpqlinux.com/mbr.html](http://www.cpqlinux.com/mbr.html)

Basically "fixmbr" or "fdisk /mbr" just copy a default mbr to the first 446 bytes of your hard-disk. Be careful not to overwrite the bytes 447-510, which is the partition table. (You would lose your partitions.)

In the above link there are a couple of default mbr:s, and they also tell how to copy a new mbr using dd-command...

Or you could make a ~100MB partition and install GRUB there...

---

