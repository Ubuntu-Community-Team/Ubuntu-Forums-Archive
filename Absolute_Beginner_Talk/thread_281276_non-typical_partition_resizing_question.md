---
title: "non-typical partition resizing question"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by johnnyboy on 2006-10-20
Much reading - no threads pertaining to my question that I could find.

I have two Op. systems on one computer.  Ubuntu with 45 gigs and windows xp with 10 gigs.  I want to shrink my ubuntu partition from 45 to 40 and enlarge my xp from 10 to 15 gigs.  Does anyone know how to do this?

I have gparted on linux.  I am considering trying just cutting some space off of the linux partition, formatting it to the win format (ntfs), and then attempting to resize the windows partition using the newly allocated space.  However if after I cut off the extra space, and reformat, I am afraid it will be put into a new partition, and will be unusable on my existing xp partition.  Will this happen?

---

### Post by CatKiller on 2006-10-20
Yes, what you were suggesting in your last paragraph **will** create a new partition.

Don't use GParted in your normal Linux environment - it's asking for trouble. Either use the live cd you used to install from, or download the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") to get the latest version. I'd advise the latter, since you want to move and ext partition.

Then you need to resize the Linux partition(s) at the right-hand end to reduce their size, then move them to the right, and then expand your NTFS partition. Assuming that your NTFS partition has a lower number than your Linux partitions. Otherwise, it's different ;)

It should go without saying that if you have any important data on this drive, you should **back it up**.

Good luck.

---

### Post by Jorge on 2006-10-20
Important: be aware that Grub loader needs to point to a specific partition number (except on Edgy, which uses a different method). For example: if you insert a new partition, the Ubuntu partition could move from "hd0,1" to "hd0,2". You would need to edit the menu.lst for Grub in order to start your Ubuntu system, otherwise it will never start.
Maybe you would prefer to resize the Ubuntu partition, and recover some space  at the end of the existing partition, assign it as a FAT or NTFS partition and use it from Windows (you can use it for storage or even for installing programs, as a "different" disk.

Good luck!

---

### Post by johnnyboy on 2006-10-21
I appreciate the help... the more current version of gparted did allow the move option, which is unavailable in the more dated version.  I shrank hda1 (linux), moved hda2 to the left so that the new unallocated space was following it, and then extended the hda2(windows) partition.  As easy as 1,2,3.

Thanks.

---

