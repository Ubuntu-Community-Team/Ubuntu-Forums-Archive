---
title: "Cloning Primary harddrive..."
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by Rocketeer on 2006-09-16
Ubuntu (LAMP) Server 6.06 needs new harddrive:
Hello, currently my System is running great and fast, but it seems i need to replace the harddrive. The primary harddrive ist currently 60GB and the new one will be 120GB - However, just adding the HD will be not enough cause the 60GB HD is dying I think. So I need an easy way to clone the 60GB HD on the 120GB HD, so I just can unplug the 60GB one and let the system run again. Is there somewhere a howto or something similar?
(Please no GUI apps, only Console available [SSH])

Bonus question: Once in a while I found an utility, where it showed the errors of a HD.... can somebody help me finding it again?

---

### Post by nereid on 2006-09-16
Just use tar to zip the whole harddrive into a single file and save that file on the new harddrive. You can unzip the file there and reinstall GRUB on this HD, voila old system on a new drive.

EDIT: Maybe you need to adjust your fstab a little bit.

---

### Post by Rocketeer on 2006-09-16
erm... sorry, but i do not like that method... i am able running both harddrives at the same time, so maybe is there some other possibility? I mean, 
on /dev/hda i have 3 (or 4) partitions, which I all want to keep. except the root partition will get bigger.

Any solutions?

---

### Post by nereid on 2006-09-17
What's wrong with this method? Instead of zipping the hole thing up, just copy them from drive a to b. There is nothing more to it (maybe creating the partitions you want on the other drive).

---

