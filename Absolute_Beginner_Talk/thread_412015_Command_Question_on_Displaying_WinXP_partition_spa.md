---
title: "Command Question on Displaying WinXP partition space"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-17
df -h command shows me what is on my **Linux** partition and their spaces, right?
I would like to know the command that displays both **WindowsXP** and linux, the spaces they occupy, and any other additional partitions that I may make in the future, in the hardrive.

Additionally, It would be wonderful if someone could tell me what the heck **/dev/hda2** ,**/dev/hda1** is?

and what is **ext3**? Isn't that supposedly the name of the **linux partition**? then why is it displayed as **/dev/hda2** in the **df -h command**?

Thank you to anyone who offers anything :]

---

### Post by taurus on 2007-04-17
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

/dev/hda1 stands for first partition of the first harddrive where /dev/hda2 is the second partition of the same harddrive.

ext3 is the default filesystem for Ubuntu where ntfs is the default filesystem for Windows XP.

---

### Post by LaRoza on 2007-04-17
/dev/anything 

anything is a disk or "DEVice"

Ext3 is the formatting, like FAT32 or NTFS.

/dev/hda1 is your hard drive partition, probably what Windows calls "c:\"
/dev/hda2 is the hard drive partition, probably "d:\"

---

### Post by Parasitesss on 2007-04-17
ohh thankyou.

---

### Post by Cypher on 2007-04-17
If you mount your Windows partitions in Linux, then the "df -h" command will show you the space available on those partitions, as well as, the Linux partitions. DF only knows about what's mounted.

Anything that starts with "/dev" is a virtual device that is used to access physical hardware. The accepted standard from the Kernel folks is to use "hda" to indicate IDE(PATA) drives, "sda" is used to indicate SCSI drives. However, you will find that SATA also uses "sda", as do USB Flash drives. So there's quite a bit of overlap here.

The numbers that follow these devices just indicates the partition.

EXT3 is a new version of EXT2 (The original Linux filesystem) that adds journling support. There are other filesystems that Linux can use, one of the other being ReiserFS.

EXT4 is in development and will build on EXT3's journling and include some performance imporvements similar to ResierFS.

Regards

---

