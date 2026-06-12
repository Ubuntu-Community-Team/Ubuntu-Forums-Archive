---
title: "best filesystem to use on a usb hard disk"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by loza on 2008-01-16
Oh Hello there ):P

I have some of hard disk drives lying about and I have decided to put them to good use by installing them into some external usb caddies so I can backup my data and have my data on the move and so on...

I have two Linux systems I will be plugging these drives into and it seemed logical to format them to a native fs. 

I just want to know as to what is the best file system to format these drives to.

I have 2 x 40G, 1 x 60G and 1 x 10G drives.

I thought it would be neat to format them to ext3 as this would stand a chance of recovery if a drive went corrupt. However when I plugged one drive in and tried to copy a file to it, the system said I was unable to, and it was right!

So I was thinking of formatting the drives to FAT32 to get round the mounting problem. But have read this is really an inferior fs as compared to ext2 or ext3.

Does anyone have a view on the best fs in this situation?

I don't think I will have the urge to use these drives on a windows system.

best regards

loza

---

### Post by wolfen69 on 2008-01-16
i have my external drive formatted to fat32 for convenience sake. it may be "inferior", but i havnt had any problems with it.

---

### Post by Irony on 2008-01-16
ext3 works fine - you probably have to set your permissions to copy to it.

Thus once it mounted open a terminal and type;

```
gksudo nautilus
```

The go to the drive and right click on it and click properties and set the permissions to your username with read and write access.

---

### Post by Hospadar on 2008-01-16
If you arn't using these drives with any windows machines (or at least not frequently) then I'd definately go for ext3

How did you format the drives? with gparted?

---

### Post by tigerplug on 2008-01-16
+1 for ext3

---

### Post by loza on 2008-01-18
> **Hospadar said:**
> If you arn't using these drives with any windows machines (or at least not frequently) then I'd definately go for ext3

How did you format the drives? with gparted?

It was indeed gparted! I think that program's really good - it makes life so easy!


Irony - Thanks you solved my problem!

I didn't mean to tread on anyone's sensibilities when I said FAT was inferior, it was just when I read round the Internet, many of the technical sites seemed to either express this or hint at it as compared to ext3.

best regards

loza

---

### Post by monte48lowes on 2008-01-18
> **loza said:**
> I didn't mean to tread on anyone's sensibilities when I said FAT was inferior

I don't think you'd offend anyone around here. I formatted my external to ext3 as well. I don't trust fat32 since the time a drive of mine corrupted and I had to dig really hard to recover over 10,000 family photos.

+1 for ext3

BTW there are utilites to use ext3 with windows, if that's necessary.

Mike

---

### Post by loza on 2008-02-06
> **monte48lowes said:**
> 
+1 for ext3

BTW there are utilites to use ext3 with windows, if that's necessary.

Mike

cool thanks 4 the info!

loza

---

### Post by jordanmthomas on 2008-02-06
My 400GB external drive is formatted with ext3 and for me at least, it performs better than the ntfs it came with.  ntfs-3g had a nasty habit of using 100% of my CPU very often.
[http://www.fs-driver.org](http://www.fs-driver.org)
^^ an ext3 driver for windows.  It's meant for ext2 but works with ext3, it just doesn't use the journaling feature, so if it gets uncleanly unmounted, you'll need to run e2fsck on it.

---

