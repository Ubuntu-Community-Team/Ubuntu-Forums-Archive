---
title: "Best Vista dualboot option?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-04-20
Which dual-boot option would be best for Feisty and Vista?
Have 2 hdd, plenty of room on both.
Vista is installed on hda (120G), hdb is empty (320G).

#1--Shrink hda with Vista and install Feisty there, or
#2--Leave hda alone and format hdb to ext3 and install Feisty on a partition there.
Also; What kind of grub/Vista mbr problems can I expect?
 Thanks for your ideas.

---

### Post by Zuph on 2007-04-20
Neither is any better an option than the other.  Obviously, whenever you shrink another partition, you're going to risk losing the data on the partition, so if you choose to shrink vista, you should back up anything important.  Other than that, there is no wrong choice.

I'm not sure what issues you need to expect as I haven't had any.  Maybe someone else can chime in there.

---

### Post by Milt888 on 2007-04-20
"I'm not sure what issues you need to expect as I haven't had any.  Maybe someone else can chime in there."

Just wondering, from your statement, are you dual booting with Vista/ubuntu?
Reading around it looks like the Vista mbr gets overwritten by grub and I didn't want to trash Vista.(Wife's)
Thanks..

---

### Post by at0mic on 2007-04-20
I am also considering installing fiesty. i would use an old ide drive for it. i just want and need to know if the new grub can handle vista or not. Anyone dare attempt yet?

---

### Post by JohnUK89 on 2007-04-20
Just so you know, there are currently NO linux partitioners that can correctly edit a Vista partition. If you try resizing the Vista partition using the Live CD it will most likely cause data loss. If you are going to resize, do it using Vista's built in disk management tool (right click the partition and click Shrink).

The version of GRUB that Ubuntu comes with will detect the Vista bootloader and insert an entry for it in the list of OS's it creates. If the worst comes to the worst and you lose your ability to boot Vista, you can boot the Vista DVD, go to the recovery section and repair the bootloader. This will remove your ability to boot Ubuntu but you can just reinstall GRUB from the Live CD in that case :)

Personally I would go for the first option, ensuring that the partition is shrunk with Vista (as explained). hdb can be formatted as FAT32, so you can share data between Vista and Ubuntu as needed, or you can install ntfs-3g and format it as NTFS. The latter option (hdb as NTFS) will require you to dig around in /etc/fstab though.

---

### Post by Milt888 on 2007-04-20
> **JohnUK89 said:**
> Just so you know, there are currently NO linux partitioners that can correctly edit a Vista partition. If you try resizing the Vista partition using the Live CD it will most likely cause data loss. If you are going to resize, do it using Vista's built in disk management tool (right click the partition and click Shrink).

The version of GRUB that Ubuntu comes with will detect the Vista bootloader and insert an entry for it in the list of OS's it creates. If the worst comes to the worst and you lose your ability to boot Vista, you can boot the Vista DVD, go to the recovery section and repair the bootloader. This will remove your ability to boot Ubuntu but you can just reinstall GRUB from the Live CD in that case :)

Personally I would go for the first option, ensuring that the partition is shrunk with Vista (as explained). hdb can be formatted as FAT32, so you can share data between Vista and Ubuntu as needed, or you can install ntfs-3g and format it as NTFS. The latter option (hdb as NTFS) will require you to dig around in /etc/fstab though.

Thanks. Good info.
Seems like a lot of people are having trouble with bootloaders and Vista.

---

### Post by bodean on 2007-04-20
> **Milt888 said:**
> Thanks. Good info.
Seems like a lot of people are having trouble with bootloaders and Vista.

Yes, there are a lot of problems with the dual boot.  I'm kind of disappointed.  This is my first attempt at running UBuntu, and wasn't aware of all the side installs that you have to do to get stuff working.  Unlike windows that basically worked out of the box, 1) dual boot is broke for getting into vista, 2) Wireless USB mouse doesn't work, 3) I'm limited to 1024 resolution and 50hz for my geforce go7400 video card which makes the os look awful.

---

### Post by Milt888 on 2007-04-20
Yeah,; seems that the problem is with the Vista bootloader and not Ubuntu.
I dualbooted XP and Edgy on my older machine and had no problem at all.
There seem to be all kinds of workarounds after the fact, ie. after either Vista or Ubuntu fails to boot, but being pretty green, none of them appeal to me.

---

