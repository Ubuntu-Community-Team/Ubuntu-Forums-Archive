---
title: "Uninstall Ubuntu from Mac...."
date: 2007-07-06
forum: Apple Intel Users
---

### Post by hellomatts on 2007-07-06
Hi,

I'm trying to remove Ubuntu from my mac as I now have it running on my machine at home and also I would rather run it from vmware...

I figured that simply running bootcamp from my osx to restore my partition would do it, but when I try to run boot camp I get the following message:

"Your startup disk cannot be partitioned or restored to a single partition.
Your startup disk must be formatted as a single Mac OS Extended (Journaled) volume already partitioned by Boot Camp Assistant for installing Windows."

Any ideas on how I might resolve this without having to format re-install?

Thanks!

---

### Post by cyberdork33 on 2007-07-06
You will first have to delete the ubuntu and swap partitions to create free space, then use diskutil (maybe bootcamp if there are no other partitions anymore?) or parted to resize the hfs partition to the whole disk again.

---

### Post by hellomatts on 2007-07-07
What is the best way to remove these partitions? If I try to run disk utility from the osx boot cd, it indicates that it will erase all three partitions... And that's the last thing that I want to do...

---

### Post by ronocdh on 2007-07-07
> **hellomatts said:**
> What is the best way to remove these partitions? If I try to run disk utility from the osx boot cd, it indicates that it will erase all three partitions... And that's the last thing that I want to do...
You could insert the Ubuntu installation CD (I prefer the alternate) and delete the partitions there (make sure to confirm your changes), then exit the installer and reboot to OS X. Hopefully then Disk Utility will be able to reclaim that free space.

---

### Post by cyberdork33 on 2007-07-07
> **ronocdh said:**
> You could insert the Ubuntu installation CD (I prefer the alternate) and delete the partitions there (make sure to confirm your changes), then exit the installer and reboot to OS X. Hopefully then Disk Utility will be able to reclaim that free space.

You might even try the gparted live cd. I don't know how good it would be at resizing your hfs partition (I know it can do it, i just don't know how safe it is), but I know you can graphically edit / delete the other parititions

---

