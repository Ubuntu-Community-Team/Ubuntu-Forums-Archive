---
title: "Boot from (not on) an ipod"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by iequalshane on 2007-04-11
I have an 40 gig ipod that has a fat32 partition.  I want to install an Ubuntu boot on the currently existing partition so that I could plug it into any machine that allows a boot from USB/Firewire and run the OS from it.  

Is it possible to do this without corrupting the functionality of the ipod at all?  Also as the title states I do not want to boot linux -on- the ipod, just from it.  To clear that up, I don't want to run the the OS on the ipod itself.

---

### Post by caffienefree on 2007-04-11
I think I understand what you mean. Is this close to what you need? You're going to need to adjust it slightly for the iPod, but it should be a similar concept?

[http://technowizah.com/2006/11/ubuntu-how-to-ubuntu-edgy-from-usb.html](http://technowizah.com/2006/11/ubuntu-how-to-ubuntu-edgy-from-usb.html)

---

### Post by iequalshane on 2007-04-12
That is close to what I need.  I guess it's not possible to install it on the already existing fat32 partition?

---

### Post by caffienefree on 2007-04-12
I don't really know. Why don't you want to reformat it as ext3?

---

### Post by iequalshane on 2007-04-12
I want to use the same storage space for storage as a windows external device, a working ipod and a linux boot partition if possible.

---

### Post by l951b951 on 2007-04-12
> **iequalshane said:**
> I want to use the same storage space for storage as a windows external device, a working ipod and a linux boot partition if possible.

I don't know if the Ipod will give you fits with an ext3 filesystem, but you can use the ext3 with windows.   [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by iequalshane on 2007-04-13
The reason for keeping the Fat32 is in hopes that I wouldn't have to format my ipod.  I have a lot of music from CDs I've lost over a couple years of moving between apartments and I don't want to lose that music on my ipod.

---

### Post by caffienefree on 2007-04-13
You could resize the FAT32 partition, and format the rest for linux.

---

### Post by iequalshane on 2007-04-13
Think that would break the ipod?

---

### Post by seshomaru samma on 2007-04-13
the ipod was not meant for these things
i'm not saying it's not possible
but if you do try it - back up your music

---

