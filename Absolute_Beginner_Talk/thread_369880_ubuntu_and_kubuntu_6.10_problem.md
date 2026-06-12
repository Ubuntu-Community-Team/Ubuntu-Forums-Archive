---
title: "ubuntu and kubuntu 6.10 problem"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by unreal1171 on 2007-02-25
as of right now i have been having an issue installing either ubuntu or kubuntu, i have 3 hard drives in the ide0 master, slave and ide1 slave. another hard drive in an ata controller and 1 sata drive. The current windows i am using is xp pro and it is installed on the hd0 master, the only way i was able to get grub 1.5 to work enough to load the os was to unplug all my drives except the sata, to get the mbr correct, everytime i tried to dual boot with windows windows is not found and i have to revert back to loading a xp cd and fixing the mbr just to load windows. i have tried doing it off the livecd but it doesnt save, it says linux is installed grub to hd0 but when i want to load linux i have to manually switch it everytime to hd0,5 it says its hd3,5, which doesnt work. i cant seem to change the menu.1st in the terminal and at this point i cant think of anything else to do, i tried gedit and when i did a sudo fdisk -lu i cant see everything for it displays so big all my drives that i cant see some because they scroll to quickly.... any help would be good. i wanted to take my raptor sata drive and use it for windows and kubuntu dualboot but i wanted kubuntu on the drive first.

---

### Post by moshuptrail on 2007-02-25
First, I think you'll get better response if you break down your problems into simple posts address one at a time.  A little punctuation would help readability a lot too.

I'll try to sum up and you tell me how I do.

1. having difficulty with dual boot
    a. this will take some effort, start by posting contents of /etc/fstab

2. can't edit menu.lst in terminal
     a. from terminal, type gksudo gedit /boot/grub/menu.lst

3. display from fdisk -lu scrolls off the page too quickly
    a. try fdisk -lu | more

---

### Post by unreal1171 on 2007-02-25
> **moshuptrail said:**
> First, I think you'll get better response if you break down your problems into simple posts address one at a time.  A little punctuation would help readability a lot too.

I'll try to sum up and you tell me how I do.

1. having difficulty with dual boot
    a. this will take some effort, start by posting contents of /etc/fstab 
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ca3b6e3f-43b6-4d17-9c77-8d8184412bc6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1d705c06-80fd-40aa-a3ed-5951d268cda8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


> 
2. can't edit menu.lst in terminal
     a. from terminal, type gksudo gedit /boot/grub/menu.lst
still doesnt seem to do anythng, cant edit it with this command or any other off the live cd.

> 
3. display from fdisk -lu scrolls off the page too quickly
    a. try fdisk -lu | more
> ok after doing this one im not sure if it did or not but it only showed 3 drives, my hda, hdb , and my sda, there was another drive on an ata controller but nothing showed up, it isnt important now but just a mention.
i have tried the code 
```

sudo grub
find /boot/grub/stage1
root (hd0,5)
setup (hd0)
quit
```

and that worked, well it said it passed, then gave a grub error on bootup.

---

