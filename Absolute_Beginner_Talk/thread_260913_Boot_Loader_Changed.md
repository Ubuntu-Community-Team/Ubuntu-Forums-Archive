---
title: "Boot Loader Changed"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by rockstar on 2006-09-19
Somehow my Windows XP Professional dissapeared from my GRUB.  I tried to edit it with /boot/grub/menu.lst but my access is denied.  Why is my access denied? How can I get my boot loader back to normal?

---

### Post by Brunellus on 2006-09-19
> **rockstar said:**
> Somehow my Windows XP Professional dissapeared from my GRUB.  I tried to edit it with /boot/grub/menu.lst but my access is denied.  Why is my access denied? How can I get my boot loader back to normal?
you need root access to edit it.  prefeace the command with 'sudo' and give your user password.

---

### Post by LotsOfPhil on 2006-09-19
Type:

sudo vi /boot/grub/menu.lst

The access is denied because only root can edit that file.

---

### Post by rockstar on 2006-09-19
Ok, so I typed the command that just got posted.  It shows my Ubuntu Kernels but not my windows partition.  It also opened it in the terminal so I cannot edit it.  I tried to login as root but that showed a bad command

---

### Post by roger99 on 2006-09-19
Ok, so try

```
sudo gedit /boot/grub/menu.lst
```

then paste this code at the end of the menu.lst (making a backup first of course....)

```
title		Microsoft Windows
root	(hd0,#)
savedefault
makeactive
chainloader	+1
boot
```

Replacing the # int 'root (hd0,#) with the partition windows is located on.

To find out which partition windows is on do an

```
sudo fdisk -l
```

---

### Post by rockstar on 2006-09-19
When I do the fdisk command, how do I know what to put in the #?

---

### Post by xhaan on 2006-09-19
> **rockstar said:**
> When I do the fdisk command, how do I know what to put in the #?

you should see something like:

```
/dev/hdb1   *         402        6842    51737332+   7  HPFS/NTFS
```

the /dev/hd?? part is the name of the device and partition, the asterisk denotes that the partition is bootable and at the end of the line is the filesystem type.

Youre looking for a line that most likely has NTFS at the end, and has the asterisk (*)

You want the name of the device which is on that line, hda1 would be the first partition of the first drive.

GRUB identifies devices starting from zero, so hda1 would be hd0,0 and hda2 would be hd0,1 and so on.
hdb would be hd1, hdc would be hd2, etc, so when you edit menu.lst, if your windows partition is hda1, you would change that to hd0,0 in the menu.lst file.

---

### Post by rockstar on 2006-09-19
Thanks for the posts.  What is the difference between an hd and the sdc?

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    7  HPFS/NTFS

---

### Post by rockstar on 2006-09-19
After following all the posts that I recieved from many, which I am very grateful for, the following occured:

Windows showed up on the GRUB.  I selected it and hit enter. Then I got this:

[PHP]Root (hd0,1)
fileSystem type is ext2fs, partition type 0x83

Save default
make active
chainloader +1

Error 13: Invalid or unsupported executable format[/PHP]

Keep in mind, all that I did to start this chain of events was turn off the computer manually after the Updater failed to restart my computer properly.

---

### Post by roger99 on 2006-09-20
> What is the difference between an hd and the sdc?

Sd would indicate a SCSI device.  The third in your system in this case. sda, sdb n so on.

GRUB however displays things differently. Hd0 is your first disk, hd1 the next regardless of how they are connected, you could have an IDE drive and a SCSI drive, if the IDE has priority in BIOS then this would be hd0. etc.  If you have two additional SCSI devices that are not hard drives GRUB still see's the disk (sdc in your case) as hd1, regardless of whats connected in between.

Can you post the complete output of fdisk.

If you do have more than one drive and Ubuntu is on one and Windoze is on another you will have to add a couple of extra commands to your menu.lst

If you only have two drives and windows is on the second try using this code in menu.lst additional to what I posted before

```
title		Microsoft Windows
root	(hd1,0)
savedefault
makeactive

# Add the next two lines to menu.lst if the drive you want
# to boot windows off is disk 2

map		(hd0) (hd1)
map		(hd1) (hd0)

chainloader	+1
boot

```

---

