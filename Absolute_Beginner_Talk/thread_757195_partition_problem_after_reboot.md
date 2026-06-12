---
title: "partition problem after reboot"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by steinkaare on 2008-04-16
Ok so my Vista chrashed, and i rebooted the system, which worked fine. The trouble was when i restarted the computer i got the message Grub 1.5 loading. Please wait... Error 22
Ok so i reinstalled ubuntu instead, creating a 12,5 partition. Ok so i restarted again and now i could choose between Vista and Ubuntu, But it turned out Vista only got the 12.5 partition, and no access to any other partitions, Any way to solve this problem easily?

---

### Post by northern lights on 2008-04-16
How many other partitions should show? What's their format?

Does Ubuntu show all?
If so, could you post the output of ```
sudo fdisk -l
```

---

### Post by steinkaare on 2008-04-16
There are 4 showing the VistaOs, Recovery Cdrom and Cdrom0
Heres what i get

Disk /dev/sda: 250.0 GB, 250059350016 bytes
138 heads, 12 sectors/track, 294925 cylinders
Units = cylinders of 1656 * 512 = 847872 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        8659     7168000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        8659       23048    11914062+   7  HPFS/NTFS
/dev/sda3           23049      287625   219069756   83  Linux
/dev/sda4          287626      294925     6044400    5  Extended
/dev/sda5          287626      294925     6044394   82  Linux swap / Solaris

---

### Post by northern lights on 2008-04-16
The partitions formatted as ext3 will not be read by your Windows without additional software.

It not "showing" the other NTFS is strange though. In Windows, navigate to the "Run" dialog (somewhere in "Start" menu) and run "mmc". Navigate to "add/remove snap-in" and add "Disk Management".

See whether the drive exists here, and if so, right-click and add drive letter...

---

### Post by steinkaare on 2008-04-16
Ok thanks for the tip. One thing though, i downloaded two videos with utorrent without really looking at the location, now i find they are located at c:\windows
Where in the hell is that?

---

### Post by northern lights on 2008-04-16
What do you mean, "where is that?"? It's in "C:\Windows"...

How did you find out that that's where the videos are? Under what OS?

---

### Post by steinkaare on 2008-04-16
Its under ubuntu. The location is C:\windows\profiles wich i cant find.
Well back to the real problem. I only have the option to delete volume, except for the VistaOS where i have all the options

---

### Post by steinkaare on 2008-04-17
Any new tips? do i have to reinstall one more time?

---

### Post by steinkaare on 2008-04-17
bump!

---

