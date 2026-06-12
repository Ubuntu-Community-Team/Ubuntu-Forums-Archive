---
title: "Reset Master Boot Record"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-12-21
I have an IDE disk that is now an external USB drive.  GRUB occupies the master boot record from an old LINUX installation.  Is there any way I can zero out the MBR so my machine won't try and boot from it if the drive box is turned on?   

Thanks,

Don

---

### Post by steve.horsley on 2006-12-21
Try changing the last 2 bytes in the boot sector. These are 0x55AA and act as a flag to indicate htat an OS is installed. To change these, I suggest you take a copy of the bootsector like this (correct the drive ID of course):
**sudo dd if=/dev/whatever of=MBR.original bs=512 count=1**
Then make a copy
**cp MBR.original MBR.modified**
then edit the modified file with a hex editor like khexedit or ghex2 and change those last 2 bytes - any change should render the disk un-bootable.
Copy the modified file back with 
**sudo dd if=MBR.modified of=/dev/whatever**

---

### Post by mengd2002 on 2006-12-22
Thanks, that did the trick.

---

