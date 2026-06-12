---
title: "First run, some questions.(desktop,hard drive)"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by supershin on 2006-01-15
Hi all, my first post here as a new linux user. Hope to learn alot. Anyway on to my problems. 
 I've finally ran ubuntu live cd but when the desktop loaded there was a black line on the left side of the monitor and the right side seemed to be cut short(taskbar displayed half a icon). I suspect the desktop was shifted to the right but i dont know how. How to fix this? 
 Also how do i access files on my hard drive containing windows. I heard something about hda but i got lost about mounting it. :confused: 
 Can i read and write to files in linux and then read and write to files in windows without corrupting the files. eg. edit a text file in linux and view(and even edit) it windows with absolutely no problems.

---

### Post by flight_master on 2006-01-15
Hello!

Welcome to Ubuntu!

First thing: This needs to be adjust on your monitor (H-Size, and H-Location). I don't know what monitor you have, so I don't know how you'd set it - check your monitor's manual (this is done with the buttons on the front of the monitor).

For your drivers, open a Console (under accessories), and type:

```

sudo mount

```
Assuming you have two hard-drives, and installed linux on the secondary one, your primary drive is HDA, and secondary is HDB. After running mount, you can browse it like you do any other directory; just go to:

/media/<drive_value>, for instance, cd /media/hda1

A normal text file? Of course you can... I'm on a dev. team where two of us use Linux, and the third guy uses Windows... there's no problem there :D

Regards,
Christian

---

### Post by supershin on 2006-01-17
Thanks, I'll try that.

---

### Post by hen3rz on 2006-01-17
> First thing: This needs to be adjust on your monitor (H-Size, and H-Location). I don't know what monitor you have, so I don't know how you'd set it - check your monitor's manual (this is done with the buttons on the front of the monitor).

Just to add on my monitor i hold down the "select button" and it auto aligns it all for me. I have found that alot of other monitors have the same feature so i gues you could try that if your a little unsure.

---

### Post by dueY on 2006-01-17
[QUOTE=supershin]
 Can i read and write to files in linux and then read and write to files in windows without corrupting the files. eg. edit a text file in linux and view(and even edit) it windows with absolutely no problems.[/QUOTE]

If you set up a FAT32 partition then you can put a file there and read/write it from both Linux and Windows.  If the file is on a Windows NTFS partition then you can read it with Linux but you can't write to the NTFS partition (not safely, anyway).  If the file is on Linux and you are using Windows I don't know of any easy way to read the file from Windows.

---

### Post by mdsmedia on 2006-01-17
[QUOTE=supershin] Can i read and write to files in linux and then read and write to files in windows without corrupting the files. eg. edit a text file in linux and view(and even edit) it windows with absolutely no problems.[/QUOTE]
You need to be careful with reading and writing files in other operating systems.

If your other OS is Windows XP then it's probably on an NTFS formatted partition. 

Linux can read from your NTFS partition but writing to it (ie. saving the edited file to NTFS) from Linux can corrupt your NTFS partition.

Windows does not read or write Linux (Ext2/3) partitions.

---

### Post by mdsmedia on 2006-01-17
[QUOTE=mdsmedia]You need to be careful with reading and writing files in other operating systems.

If your other OS is Windows XP then it's probably on an NTFS formatted partition. 

Linux can read from your NTFS partition but writing to it (ie. saving the edited file to NTFS) from Linux can corrupt your NTFS partition.

Windows does not read or write Linux (Ext2/3) partitions.[/QUOTE]
Having said that, if your data is on a FAT32 partition you can read and write from both operating systems to and from that FAT32 partition.

---

### Post by Pulshion on 2006-01-17
Im not trying to highjack this thread. I though i can ask it here and not make another thread. Well i ran sudo mount and this is what i got 
```
dmitriy@linux:~$ sudo mount
Password:
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

```

Could you explain what those lines mean and what do i type for me to mount my C: windows partition and D hard drive
Thank you

---

### Post by jimrz on 2006-01-17
Take a look [**[COLOR="Sienna"]here[/COLOR]**]("http://www.ubuntuguide.org/#automountntfs")
for intructions on mounting your win partitions. Make sure you unmount the drives before trying to make any changes, or the changes won't take. Also, read well down the page to find the proceedure which will set the win partitions up to auto-mount each time you start linux.

---

