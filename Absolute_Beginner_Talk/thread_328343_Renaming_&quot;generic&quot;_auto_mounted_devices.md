---
title: "Renaming &quot;generic&quot; auto mounted devices?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2006-12-30
I have 2 drives that are auto mounted (not in the fstab file).

one is for my memory stick which I keep in the computer for personal information, and the other is a USB removable hard drive for all my data.

They are automatically mounted/unmounted and are labeled 'usbdisk' and 'usbdisk-1'. 

How can I rename them so when they automatically mount, they aren't these generic names?

---

### Post by alexmoon on 2007-01-15
Did you find out how to do this? I've been wondering myself, and would appreciate help.

Thanks.

---

### Post by mcduck on 2007-01-15
The trick is to rename the partitions on the portable devices. Automatic mounting uses partition names if available.

For Ext2/Ext3:
```
sudo tune2fs -L newname /dev/sda1
```
(replace name and device with the right ones)

edit: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by alexmoon on 2007-01-15
I followed the instructions on the howto ([https://help.ubuntu.com/community/RenameUSBDrive)](https://help.ubuntu.com/community/RenameUSBDrive)), and renamed the USB without any problems.

When I typed this part, "sudo mlabel i:Claes"
It said:
Total number of sectors not a multiple of sectors per track!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test

I added the line to the .mtoolsrc file and then it worked fine, but I'm quite curious about what the error means, and what I just did by adding the line. If you have any ideas, I'd appreciate being enlightened.

Thanks!

---

