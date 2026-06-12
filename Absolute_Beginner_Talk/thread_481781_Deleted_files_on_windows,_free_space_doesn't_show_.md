---
title: "Deleted files on windows, free space doesn't show up on linux"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by deepti on 2007-06-22
I have a Samsung Digital Audio Player. It is a 1GB USB drive that can also play music, etc. I think it is called YP-U2, but I'm not sure...

It is in FAT32 format.

I deleted ~700MB of files on it when connected to a Windows XP computer. 

When I connect it to Ubuntu (I'm using Edgy), the files don't show up, but I have only about 277MB of free space on the disk. There are no files in the .Trash folder. 

Using the command fdisk, it shows 738312 blocks as "Used".

On windows, everything displays correctly.

Does this problem have to do with the way Windows deletes files?

Must I format the disk to get back the free space? Will this affect the MP3 player in any way?

I use ubuntu as my primary machine... so I would really like to get all my disk space back. 

Thanks again for any help. Do let me know if you need more information.

Cheers,
Deepti

---

### Post by FleetAdmiral74 on 2007-06-22
The problem is how partitioning works. The NTFS partition your Windows uses is still the same size, so ub will read that as one whole partition regardless if it is made up of free space or FULL of data.

the trick is to defrag it, and then use gParted to resize it. That ought to do the trick.

omg, I might have totally misread the problem...

---

### Post by Motoxrdude on 2007-06-22
> **FleetAdmiral74 said:**
> The problem is how partitioning works. The NTFS partition your Windows uses is still the same size, so ub will read that as one whole partition regardless if it is made up of free space or FULL of data.

the trick is to defrag it, and then use gParted to resize it. That ought to do the trick.

omg, I might have totally misread the problem...

Resize a usb drive? Not sure that is possible with gparted or any software.

---

### Post by FleetAdmiral74 on 2007-06-22
yaya, you're right. I read it as he deleted files off his XP partition, and expected it show up as free space in Ub. Sorry for the misunderstanding, free apologies on request.

---

