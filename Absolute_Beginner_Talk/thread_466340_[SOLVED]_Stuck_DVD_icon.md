---
title: "[SOLVED] Stuck DVD icon"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-06-06
Stupid question, I was watching a movie in totem-xine and at some point to DVD icons appeard on my desktop, I dont remember what I did for that to happen. I ejected the DVD through one of the icons (and sent it back to Netflix), but the other is still there and nothing happens if I select eject.

How can I get rid of such icon?

---

### Post by p_quarles on 2007-06-06
Did you try right-clicking (or whatever the equivalent is for Mac), then choosing "unmount volume"? That should get the icon off your desktop. You might also be able to delete the icon from the desktop folder in your home directory.

---

### Post by jdrodrig on 2007-06-06
Hi, thank for the quick reply...

the umount option does not appear (see below) and neither the icon appears in desktop to be deleted (see below)...

Any other suggestions?

---

### Post by p_quarles on 2007-06-06
Eesh. That's strange. Have you tried unmounting from the terminal?

---

### Post by jdrodrig on 2007-06-06
Only because it is a begginners section I do not feel that bad in asking, "how do I do that?"

a sudo fdisk -l gives
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5607    45038196    7  HPFS/NTFS
/dev/hda2            5608        7219    12948390   83  Linux
/dev/hda3            7220        7296      618502+   5  Extended
/dev/hda5            7220        7296      618471   82  Linux swap / Solaris

And in /media I have
jdrodrig@Trino-Ubuntu:/media$ ls
cdrom  cdrom0  trino_win  win_trino
jdrodrig@Trino-Ubuntu:/media$ 

thanks in advance...

---

### Post by p_quarles on 2007-06-06
Hmm.. fdisk is saying your DVD drive is empty, I think.

And, after thinking about it again, I don't think you want to unmount, since that might disconnect your DVD drive (I'm a noob, too). Take a look at this post:
[http://ubuntuforums.org/showpost.php?p=2776225&postcount=21](http://ubuntuforums.org/showpost.php?p=2776225&postcount=21)

You might be able to get the icon off by following that person's suggestions for commenting out a device. If that doesn't work, this is beyond my knowledge.

EDIT: Of course, you could also run (terminal) $ eject /media/Casino_Royale but I imagine that would have the same effect as ejecting it from the icon. Worth a try, though.

---

### Post by SPace_Pirate_Arrr on 2007-09-22
I have the same problem.  Somehow the same DVD icon appeared twice on my desktop, then only one of the two could be removed by ejecting.  (I have only one optical drive).  Any help fixing this would be greatly appreciated.  

EDIT:  The link above worked for me, though I'm sure there must be a better way than taking it out of the fstab.

---

### Post by dogscoff on 2008-03-27
Same problem here on Gutsy 64. DVD in question was from the Alias Box set (Yeah, i know, but I'm hooked!). 

Editting the fstab file as per the link above fixed the problem for me. Normal functioning is resumed :-)

---

