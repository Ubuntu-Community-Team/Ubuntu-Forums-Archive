---
title: "[SOLVED] drive icons on desktop"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-17
I have been trying to get my internal drives automounted so that I have an icon for each on the desktop. Although they mount properly at their mount points under /mnt, I do not get the drive icons on my desktop.


Can someone help me get those on the desktop?

---

### Post by alienexplorers on 2007-06-17
You can try going into the configuration editor under nautilus, then desktop and turning on computer icon.

---

### Post by bronxNZ on 2007-06-17
I'm realitively new to this but if you are trying to get your windows drive to automatically show up the you can use the following tutorial.

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

This talks you through step by step how to get NTFS drives to show up. It worked for me :)

---

### Post by Inxsible on 2007-06-17
> **bronxNZ said:**
> I'm realitively new to this but if you are trying to get your windows drive to automatically show up the you can use the following tutorial.

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

This talks you through step by step how to get NTFS drives to show up. It worked for me :)

Thanks, but I have an EXT3 hard drive, which has my movies and music. I dont want my gf to go into the FileSystem as she doesnt need to see any of that. 

I want her to see the drive on the desktop so she can directly go to it. I know we can create shortcuts or a bookmark, but previously my drives mounted properly. Now suddenly they don't :(

---

### Post by Inxsible on 2007-06-17
> **alienexplorers said:**
> You can try going into the configuration editor under nautilus, then desktop and turning on computer icon.

Thanks, but that still takes you to the FileSystem not to the drive directly.

---

### Post by alienexplorers on 2007-06-17
If you go to the Applications>System Tools>configuration editor.  Then open up apps and goto nautilus.  At nautilus select desktop.  There is a check box to enable Volumes Visible.  Have really never tried putting other drives on the desktop so this is just a good guess.  Sorry.

---

### Post by arvevans on 2007-06-17
File mounting is controlled by a listing that resides at /etc/fstab.
You can add entries to /etc/fstab by using the information from "man fstab" and "man mount".  If you put the info in /etc/fstab your drives will be mounted at boot time.  If you want to mount drives under manual command, you can do that with the "mount" command.

Yes, I know that this method requires use fo the dreaded "CLI" (Command Line Interface", but that is the most efficient way to make sure your fstab file is correct and to make changes to it.

Depending on which X-window version you are running, you may still have to make a link to your mounted drives so that its icon will show up on your Desktop screens.
_._

---

