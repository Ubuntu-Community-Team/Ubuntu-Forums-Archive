---
title: "Hard drive issues"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by viergeame on 2007-05-09
I have three hard drives on my computer; my linux drive, my windows drive, and an external one that almost always stays with this computer.  
Recently I started having problems with my windows and external drives.  At first I suddenly had no write permission for either of them, they had been fine for several weeks but one day the permissions somehow got changed.  Now in the past few days my external one will not even mount.  
I tried every solution I could find for changing the permissions, and nothing seemed to have any effect.  A friend of mine suggested creating new mount points, but I didn't get anywhere with that either.
One thing that I think may be causing problems with the external drive is that it is formatted for FAT32, and from what I can tell FAT32 doesn't get along with Linux very well.  My windows drive is NTFS though.
I'm completely lost on what to do at this point.  Usually I enjoy working out my computer problems but this one is fast losing it's charm.

---

### Post by spin2cool on 2007-05-09
This section has details for correctly mounting other filesystems, either per-use, or on boot.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

I think you're mistaken - Fat32 and linux should get along just fine

---

### Post by viergeame on 2007-05-09
So I should just make new mount points for them both?  

My NTFS drive has permission problems but it mounts on boot and all that just fine.  Is there any way to just change the permissions on it?  Somewhere I read a suggestion to use "chown" to fix it but that didn't seem to do anything.

---

### Post by Einsam71 on 2007-05-11
Being new myself i cant help you with the FAT32 drive, but as for the permission problem in the NTFS drive i just downloaded NTFS config tool from add/remove programs and it fixed it for me. Search for " NTFS"  in add/remove programs.

---

