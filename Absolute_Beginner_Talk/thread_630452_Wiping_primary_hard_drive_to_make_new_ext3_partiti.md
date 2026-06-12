---
title: "Wiping primary hard drive to make new ext3 partition - will it still boot?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Griffiss on 2007-12-03
Hi

I'm thinking of wiping my primary hard drive (currently has windows on NTFS partition) to make a new ext3 partition. I'm not sure how this will work with GRUB.

The way I understand it is that Grub is on the first sector of my primary (master) hard drive. If I use gparted to reformat this whole disk as ext3, will my system still boot afterwards?

Ubuntu is on my second hard disk.

Thanks,
Griff

---

### Post by Irony on 2007-12-03
Formatting your first hard drive doesn't format the mbr so it will boot up fine if you format it as ext3.

---

### Post by Griffiss on 2007-12-03
Ok thanks.

So the MBR is on the first sector of the primary hard drive but formatting this drive simply won't touch it?

---

