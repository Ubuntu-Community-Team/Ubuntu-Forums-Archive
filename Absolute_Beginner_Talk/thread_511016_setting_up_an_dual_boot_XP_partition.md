---
title: "setting up an dual boot XP partition"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-07-27
the threads i've read don't quite answer my question, but they sort of nearly do.

what i'm wondering is how easy would it be to set up a small XP partition as a dual boot ?

i'm just wondering if it would be a problem since i've got Ubuntu installed and set up and use it on a daily basis, and i don't particularly want to re-format if I can help it.

i've got about 110gb free on my hard drive, so i was thinking of maybe partitioning off 10gb just really to let me play a few games in it that 'wine' doesn't yet cope with.

is it as simple as running a command to partition off the space, then rebooting into it ?

and if i wanted to delete the partition afterwards, is that do-able as well ?

is there a good idiot guide I could read to get an idea of how to proceed ??

thanks.

---

### Post by cek on 2007-07-27
You can resize your partitions with gparted -- should be in add/remove programs, search for it.

Once the partition is resized, you can simply install XP on the new partition.  Be very careful in the XP setup to choose the proper partition so that you don't format any of your Ubuntu partitions...

Also, the XP install will overwrite your master boot record -- effectively not allowing you to boot into Ubuntu.  You will have to reinstall Grub by booting up your Ubuntu Live CD.

---

### Post by NESFreak on 2007-07-27
you'd need to free some space on your hard disk using (g)parted. Since the partition you probably want to resize is the one containing your os, this has to be done from the live cd. Make sure that there is room available for a primary partition (a single harddisk can hold up to 4 primary partitions (which in turn can contain secondary partitions.)
Install windows XP on the empty space you just created. The windows installer will overwrite your mbr, so you would have to reinstall grub from the live cd. [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by jasonwatkins on 2007-07-28
i made a slight mistake of deciding to partition off 30gb, so it took frikkin' hours to do, but hey, it's all done and it's all working.

which means i've done something wrong :D

---

