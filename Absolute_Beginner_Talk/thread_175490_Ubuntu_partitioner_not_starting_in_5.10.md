---
title: "Ubuntu partitioner not starting in 5.10"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Quacky on 2006-05-13
Greetings

Long story short: 
Everything works fine until the partitioner. "Starting up the partitioner" loads completely, but when it's done the only thing I see is a blue screen with a grey text input field at the bottom. If I press ctrl+c I get the "Starting up the partitioner" screen back, frozen to 52%.

Troubleshooting: 
Nothing wrong with the CD's. Checked the md5 and burned the .iso multiple times on different CD's with the slowest possible speed. 
Searched for similar problems. Found some bug reports, but it seems that the reason for those was mainly RAID. Mine is isn't that complicated, just two hard drives, nothing fancy.
Tried 5.04, installation was smooth and it worked fine. I'm intimidated by the 5.04 -> 5.10 update, therefore I'd rather just reinstall straight to 5.10.

Hardware:
Nothing special here.
MSI 875P with P4 2,6Ghz Intel
Two hard drives. Diamondmax 160GB, DMA133 with Windows XP (NTFS). Then an older ~20GB hard drive currently running 5.04 Ubuntu.

If needed, I'll happily give more info. I'm a bit lost at the moment, especially since I can get the 5.04 up and running, but not the newer one.

---

### Post by stevenash on 2006-05-14
[QUOTE=Quacky]Greetings

Long story short: 
Everything works fine until the partitioner. "Starting up the partitioner" loads completely, but when it's done the only thing I see is a blue screen with a grey text input field at the bottom. If I press ctrl+c I get the "Starting up the partitioner" screen back, frozen to 52%.

Troubleshooting: 
Nothing wrong with the CD's. Checked the md5 and burned the .iso multiple times on different CD's with the slowest possible speed. 
Searched for similar problems. Found some bug reports, but it seems that the reason for those was mainly RAID. Mine is isn't that complicated, just two hard drives, nothing fancy.
Tried 5.04, installation was smooth and it worked fine. I'm intimidated by the 5.04 -> 5.10 update, therefore I'd rather just reinstall straight to 5.10.

Hardware:
Nothing special here.
MSI 875P with P4 2,6Ghz Intel
Two hard drives. Diamondmax 160GB, DMA133 with Windows XP (NTFS). Then an older ~20GB hard drive currently running 5.04 Ubuntu.

If needed, I'll happily give more info. I'm a bit lost at the moment, especially since I can get the 5.04 up and running, but not the newer one.[/QUOTE]
I'm having the exact same problem.  I have 512mb of RAM.  Anyone have any solutions?

---

### Post by stevenash on 2006-05-14
I think that it has something to do with having 2 hard drives.  Every thread I've seen where someone has this same issue, they have 2 hard drives.  I have one 40GB hard drive I have Windows installed on, then a brand new hard drive with 250GB of unallocated space that I'm ready to partition and put Ubuntu on.

Also, when I was trying out Ubuntu with the LiveCD, the startup would stall during "Starting Volume Enterprise Management," but I could hit Ctrl+C and got past it.  I think this may have something to do with the problem, too.

Does anyone have ANY suggestions?  Please.  I really don't think that its a problem with the install CD.

---

### Post by cyber0 on 2006-05-14
[QUOTE=stevenash]I think that it has something to do with having 2 hard drives.  .[/QUOTE]

I'm getting the same error message with a single hard drive.  Initially I tried installing it on a 2.1 gig h/d which installed fine other than it ran out of room when installing some of the final packages.  I could log in etc.

My 10 gig drive hangs at the 52% partitioner stage.

This would seem to indicate it is hard drive related.  The 10 gig drive worked fine with windoze.

---

### Post by cyber0 on 2006-05-14
I'm feeling pretty pleased with myself!  (doesn't take much).

I've just run the fdisk.exe supplied with windoze 98 and deleted all partitions on my drive and retried the Ubuntu installer and it's worked beautifully!

Definitely worth a try.

---

### Post by stevenash on 2006-05-14
[QUOTE=cyber0]I'm feeling pretty pleased with myself!  (doesn't take much).

I've just run the fdisk.exe supplied with windoze 98 and deleted all partitions on my drive and retried the Ubuntu installer and it's worked beautifully!

Definitely worth a try.[/QUOTE]
Interesting.  I have 2 hard drives, the first has only 1 partition which is entirely taken by Windows XP. Obviously I don't really feel like formatting that one.  My 250 GB drive has no partitions on it and is completely unallocated, so I don't really have any partitions to delete.

Any suggestions?

---

### Post by cyber0 on 2006-05-14
You've probably tried this but . . .

I'd remove the XP disk and make the blank 250 gig drive the primary drive and try that.  Can't think of anything else but I am a total novice at this :)

---

### Post by stevenash on 2006-05-14
[QUOTE=cyber0]You've probably tried this but . . .

I'd remove the XP disk and make the blank 250 gig drive the primary drive and try that.  Can't think of anything else but I am a total novice at this :)[/QUOTE]
I thought about that.  If I just unplug the 40GB drive it may work.  Does anyone know how that will affect installing GRUB and creating a Dual-boot system?

---

### Post by Quacky on 2006-06-04
Yay, 6.06 works. Although I got some "Buffer I/O error on device dm0, logical block xxxxxx" messages.

---

