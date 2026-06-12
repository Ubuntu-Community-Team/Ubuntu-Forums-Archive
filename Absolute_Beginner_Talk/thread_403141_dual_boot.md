---
title: "dual boot"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-04-06
i have that 


Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         500     4016218+  83  Linux
/dev/hdc2            9649        9729      650632+   5  Extended
/dev/hdc3             501        5059    36620167+  83  Linux
/dev/hdc4            5060        9648    36861142+  83  Linux
/dev/hdc5            9649        9729      650601   82  Linux swap / Solaris


for now i want to convert hdc4 to be ntfs and install windows xp on it 

so how can i do that ?? please list the steps one after one , and don't refer to another links

---

### Post by benerivo on 2007-04-06
Just put the XP disk in the drive and install it in to that partition, using ntfs quick format from the options. It will however make all your linux installations unbootable, although i think there may be a linux recovery cd (based on gparted) that will then allow you to reinstall the grub boot laoder so that all os's are bootable.

---

### Post by ceezax on 2007-04-06
though i want to format hdc4 with ntfs  because i don't have a bootable xp  cd

so i will start the installation from that partition after downloading the windows source into it 

so how can i format hdc4 into ntfs

---

### Post by SishGupta on 2007-04-06
sudo apt-get install gparted

system>administration>gnome partition manager

select /dev/hdc in the top right hand corner

click on /dev/hdc4 on the visual partition selector

right click>unmount

right click>format to>ntfs

click "apply" on the toolbar and accept any confirmation dialogs



Good luck on installing windows with out the windows installer. I didn't even know you could do that (and was sure you couldnt.)


Also, in the future please search the forums as there has been hundreds of threads describing exactly what i just said. You will save us and yourself a lot of time.

---

