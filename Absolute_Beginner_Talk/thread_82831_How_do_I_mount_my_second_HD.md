---
title: "How do I mount my second HD?"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-27
I have a second HD installed in my PC which is used just for data backup. How do I make it show up so I can access information from it?

---

### Post by JurB on 2005-10-27
Check out the ubuntuguide 

System -> Help -> Ubuntu 5.10 starter guide ->Windows Partitions (assuming you use Ubuntu 5.10, and not kubuntu)

---

### Post by Sheco on 2005-10-27
Do you know where to find the drive in /dev? (is it /dev/hda?) 
Do you know which partition you have to mount? (/dev/hda3?)

---

### Post by stuporglue on 2005-10-27
Run System-->Administration-->Disks

Select the Hd from the list on the left
Click the "Partitions" tab, and find the partition you want to mount. 
If the accect point is blank, click "change" and find /media and create a folder for a mount point. Make the folder's name whatever you call the disk.
Click the "enable" button below "Size" bar.

---

### Post by JurB on 2005-10-27
[QUOTE=stuporglue]Run System-->Administration-->Disks

Select the Hd from the list on the left
Click the "Partitions" tab, and find the partition you want to mount. 
If the accect point is blank, click "change" and find /media and create a folder for a mount point. Make the folder's name whatever you call the disk.
Click the "enable" button below "Size" bar.[/QUOTE]

Things just keep getting easier :)  Didn't know that :rolleyes:

---

### Post by Darrin on 2005-10-27
[QUOTE=stuporglue]Run System-->Administration-->Disks

Select the Hd from the list on the left
Click the "Partitions" tab, and find the partition you want to mount. 
If the accect point is blank, click "change" and find /media and create a folder for a mount point. Make the folder's name whatever you call the disk.
Click the "enable" button below "Size" bar.[/QUOTE]

That was easy. Thanks. Command line stuff confuses me. I like it via GUI like this. 

Its on my desktop now, but says I dont have permissions to view it. How do I change that?

---

### Post by Sheco on 2005-10-27
Nice, and there I was trying to help with the command line, that's the way I'm used to do it :)

Can't read it? I hope it is not NTFS, or is it?

---

### Post by Darrin on 2005-10-27
I was reading[ this]("http://www.ubuntuguide.org/#changefilesfolderspermissions") it looks like I just need to change ownership. This correct?
It says to type in this ```
sudo chown system_username /location_of_files_or_folders
``` so in my case since my username is darrin and the location of the folder/HD is /media/hd_backup, then in the terminal I would type in the follwoing:
```
sudo chown system_darrin /media/hd_backup
```. This appear correct?

---

### Post by Mustard on 2005-10-27
[QUOTE=Darrin]I was reading[ this]("http://www.ubuntuguide.org/#changefilesfolderspermissions") it looks like I just need to change ownership. This correct?
It says to type in this ```
sudo chown system_username /location_of_files_or_folders
``` so in my case since my username is darrin and the location of the folder/HD is /media/hd_backup, then in the terminal I would type in the follwoing:
```
sudo chown system_darrin /media/hd_backup
```. This appear correct?[/QUOTE]

I think it would be....

```
sudo chown darrin /media/hd_backup
```

Is it an NTFS file system?

I ask that because you can't write to NTFS with linux.

---

### Post by Darrin on 2005-10-27
[QUOTE=Mustard]

Is it an NTFS file system?

I ask that because you can't write to NTFS with linux.[/QUOTE]

It looks like it is :(

---

### Post by Mustard on 2005-10-27
[QUOTE=Darrin]It looks like it is :([/QUOTE]

If you are using a dual boot system and want to move files between them, you can create a fat32 partition (which both linux and windows can write to without problems) and store files you want to move between the systems in the fat32 partition.

---

### Post by Darrin on 2005-10-27
Thanks mustard. I dont have a whole lot on the extra drive so Ill probably just wipe it out and fromat the whole thing as fat32.

---

