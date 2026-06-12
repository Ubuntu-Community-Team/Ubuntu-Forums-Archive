---
title: "Viewing Files w/live cd??"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by bsj2985 on 2006-04-27
Ok  

I&#8217;m brand new to all this, ubuntu (10 min ago) and forums (2 min ago).

I originally looked into this because I can no longer boot up in windows and for some reason or another need reformat. But I have a TON of stuff I would like to save, is it possible to run the Live CD version of ubuntu and send the pictures on my hard drive to a flash drive and then PERMINITLY get rid of windows?

Any help would be greatly appreciated I have no idea what I&#8217;m doing

Thanks
Ben

---

### Post by Qrk on 2006-04-27
It is very possible, one of the great uses for the liveCD. I don't know if the Ubuntu liveCD will mount ntfs drives automatically (I haven't used the live cd for a while), but I believe it will.

Have you already booted into Ubuntu from the LiveCD? You should find windows on 
/dev/hda1 Navigating to this drive may cause the system to tell you that you don't have permissions to view the folder. Try using this:

```
gksudo nautilus
```

Paste it into the terminal ( Applications->System Tools->Terminal )

If you don't see /dev/hda1, follow this guide:

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

