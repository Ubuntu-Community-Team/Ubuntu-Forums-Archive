---
title: "partitons question"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Gstyle on 2007-11-02
How can I see my rest partitons under my computer?
I found only one called filesystem, but  in installation I made 2 more.
Please Help!

---

### Post by mikewhatever on 2007-11-02
My Computer? Do you mean in Windows? Are the partitions ext3? If all are 'yes' then XP can't see ext3 linux partitions. They appear in the Disk Management window as partitions with unknown file system, but not in My Computer. You need fs-driver to solve this [http://www.fs-driver.org/](http://www.fs-driver.org/).
Next time, please post more information about your problem.

Cheers.

---

### Post by Gstyle on 2007-11-02
I made 2 partitions and mounted them under /home and /usr .
How can I access them via Places or Computer?:confused:

---

### Post by mikewhatever on 2007-11-02
Can you post the output of fdisk -l?

---

### Post by jw5801 on 2007-11-02
If you tell partitions to mount to a certain folder (ie. /home or /usr) then they appear at that point in the filesystem. They don't appear as different "drives" as you would expect in windows. Thus in the "Computer" section under places you will only see your root filesystem. That's because this menu is created by gnome, and your /home and /usr partitions are mounted well before gnome is started, due to a couple of entries in /etc/fstab. If you insert a USB drive or something similar and let gnome automount it then it will appear separately in this menu.
If you want to check that you actually do have different partitions mounted at this point, then run gparted (the gnome partition editor) and it'll give you a nice graphical picture of your partitions and tell you where they're mounted to. fdisk -l will tell you the same thing but it's not as pretty.

---

### Post by Gstyle on 2007-11-02
Thanks for answering.
So its no way I can edit fstab as I can see them as seperate drives like in Windows under Places or Computer?

---

### Post by jw5801 on 2007-11-02
> **Gstyle said:**
> Thanks for answering.
So its no way I can edit fstab as I can see them as seperate drives like in Windows under Places or Computer?

Not by editing fstab you can't, since whether they appear in that "Computer" folder or not has absolutely nothing to do with where they mount to. You should be able to create a link to the folders they're mounted to in the folder that corresponds to that "Computer" folder if you really wanted. However lets move all discussion on this into the [one thread](http://ubuntuforums.org/showthread.php?t=600295) rather than scattering it across two.

---

### Post by mikewhatever on 2007-11-02
Well, I hope you'll have fun editing fstab in the other thread, however, how about creating simple launchers on the desktop. You can right click on the desktop and select 'Create launcher', give it a name, say Home (for /home) and the command
> nautilus /home

Clicking on it would open a file browser window to /home.

---

