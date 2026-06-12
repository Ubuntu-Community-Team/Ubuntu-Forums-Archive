---
title: "Warning! Gparted crashes sometimes"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by tomxyz on 2007-11-27
hello all,

i have an external 250g maxtor drive that was running smoothly on my kubuntu system (dapper) using the ntfs-3g driver.
After doing some minor (automatic) update (none to the ntfs-3g) I didn't have writing permission anymore not even as root. I spend about two weeks trying to solving this problem (chmod, ntfsfix,.....) without succes.

I then decided to use Gparted to reformat my external drive from ntfs to fat32 (so I can use this drive on both linux and windows systems)
Because I couldn't take a backup of all this information (no where to easely store 120mb),
I decided to shrink the ntfs partition, create a new fat32 partition, move all data from the ntfs partition to the fat32 partition, and then enlarge the fat32partition.

Somewhere in the middle of shrinking the ntfs part or making the fat32 part, something went wrong. the proces stopped and a popup window came up saying new media has been found, what you want to do, open,...,.... Below this popup windown was an error window. I cancelled the 'new media has been found' window in order to see the error window, only to find it blank, nothing written in the window.

For people familiar with the gparted interface, I now only see two black rectangles (one should have been the ntfs part, the other the fat32 part) and where it indicates the filesystem it says unknown!!

I hooked the external drive to my other computer wich is running windows xp, when I click the drive, it says Disk not formatted, you want to format it now?

My answer to that question would have to be, NOOOOOOOOOOOOOOOOOOOO!!!!

Anybody out there who might know what went wrong and how I can retrieve my data? 

regards Tom

---

### Post by master_kernel on 2007-11-27
You'll have to use a disk recovery utility like Ontrack or Systemtec. Your HD is corrupt.

Sorry,
master_kernel

---

### Post by tomxyz on 2007-11-27
nothing I can find in synaptic? is it open source this ontrack or systemtec or go out and buy it?

Tom

---

