---
title: "iPod read only problems"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by kthdsn on 2006-09-23
Firstly, apologies for starting yet another iPod thread, I have looked at previous posts but couldn't find a solution.

I picked up a new iPod today (it's a reconditioned 3rd gen one, the battery was dead in my old one) and I'm trying to get it set up in ubuntu.  Just to be clear, I didn't try to use my old one in ubuntu, I hadn't used it since my windows days.

I don't have access to windows or a mac, I don't know if that is going to make things more difficult for me, I hope not :| 

I've connected the iPod via USB.  It mounts to /media/ipod.  Rhythmbox recognises it, as does gtkpod and banshee.  I want to use gtkpod, but since it wasn't working I tried banshee as well to see what happened.

In gtkpod when I try to add music to the iPod it tells me some directories need creating on the iPod.  When I tell it to go ahead and create them, it says there was an error.

In banshee, the iPod is recognised, but the sync button is faded out and I can't press it.

In nautilus the iPod shows up with a few folders on it.  These are owned by "99" and only the owner has write permissions.  I figured this must be the problem and tried to sudo chmod to 777.  This returned read only errors and nothing was changed.

How can I stop the iPod from being read only?  I would really appreciate some help!

---

### Post by bulldog on 2006-09-23
Try  gksudo nautilus  and see if you can alter your Ipod as root.

---

### Post by Carbonbasedmistake on 2006-09-23
Did you try to open a second file browser and then simply drag and drop your music files on the PC to the Ipod? I use an Cowon IAudio and that is the way I get music back and forth. If the files on the IPOD now are not system files and are owned by 99 you may be able to right click the folders and then set permissions manually by checking boxes in the properties secton of the drop down box.

hope it helps

bob

---

### Post by kthdsn on 2006-09-23
Thanks for the suggestions, I'm unable to do either of those things.  It won't let me write anything to the iPod even as root.

---

### Post by bulldog on 2006-09-23
Could there be a lock in the firmware? Like DRM or such.

Could talk nonsens,have no Ipod or such myself,only thinking about possibility's ;)

---

### Post by kthdsn on 2006-09-23
I don't know, it's just how I picked it up from the store.  I have no idea about that kind of thing.  Thanks for trying to help, it's very frustrating ;)

---

### Post by kthdsn on 2006-09-23
OK I think I've identified the problem, the iPod is using the hfsplus filesystem instead of fat32.  Is there a way I can change this without having to resort to windows?

---

### Post by bulldog on 2006-09-23
Well if you mean to reformat it in FAT32 you can use gparted.

Be sure you unmount the Ipod before you apply your changes.

---

### Post by kthdsn on 2006-09-23
Thanks, I'll have a go :D

---

### Post by astoltz on 2006-09-23
Before you switch to FAT32, Linux should work fine with the HFS+ formatted iPod.  That said, it's a bit difficult to recover from the "read-only" problem - I've had success once and killed the iPod once.  So I've had to convert to FAT32 and that process is also a bit tricky.  The iPod firmware is on the first 32Meg of the SECOND HFS+ partition (/dev/hda2 on my machine).  You have to copy that BEFORE you switch to FAT32 otherwise you'll be left with and unbootable iPod.  ```
sudo dd if=/dev/sda2 of=backup_firmware
```
Then make two partitions: The first 32Meg leave as empty space and the second make a FAT32 partition with the remaining space.  Then copy the firmware back onto the first 32meg of free space:```
sudo dd if=backup_firmware of=/dev/sda1
```

---

### Post by kthdsn on 2006-09-23
Thank you for your help, I wish I'd read it BEFORE I just switched to fat32...

I'm at the unbootable stage, oops.  Anything I can do to recover?

---

### Post by astoltz on 2006-09-23
kthdsn, check your private messages for a link to the firmware.

---

### Post by caporaso on 2006-10-19
Nevermind, I figured out the problem. I was not using Listen correctly...

Hi:
I have what seems to be a similar problem -- I can read from my iPod both by browsing to it, and in Listen or Rhythmbox, and I can write to it by browsing to it. But, I can't write to it from Listen or GtkPod. The iPod is formatted as Windows Virtual FAT (vfat).

Anyone know what might be going on here? 

Thanks for any help!
Greg

---

