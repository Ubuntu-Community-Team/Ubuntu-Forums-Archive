---
title: "GUIDE:can you only burn cds with your dvd burner and not dvds?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by %hMa@?b&lt;C on 2007-07-24
If you have trouble burning under linux, every cd will burn but no dvd?  I have  a pioneer dvr-111d that had that exact problem.  follow these instructions for a fix! It may be ubuntu centric or maybe pioneer centric, who knows?  If this does not work, make sure that dvd drive is set up (master/slave like it should, mine is as a master)

step 1
look at your fstab file, look for the one that is for your dvd drive.  Mine is listed as cdrom0.  Make sure that if you have more than one optical drive, you know which one it is before going to step two.  (you can test by doing "sudo eject /dev/cdromX" where x is the numbers of the drives)
to look run the command 
```
cat /etc/fstab
```
and your dvd drive in the fstab file should look like this
> /dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

step 2
look for the "noauto" part of the file.  If that is there, you will need to change it to "auto". so open up your favorite text editor (for simplicity, i will use pico
```
sudo pico /etc/fstab
```
) and just delete the no infront of the "auto" so it reads something like this
> /dev/hda        /media/cdrom0   udf,iso9660 user,auto     0       0
press <ctrl>+O to save.  make sure that DMA is enabled by using ```
sudo aptitude install hdparm
sudo hdparm -d1  /dev/dvd
```
and fire up your favorite dvd burning app!  It should now work as it should

---

### Post by Al3xK3aton on 2007-07-24
That guide doesn't say how to mod a CD burner to burn/play DVDs. Any advice?

---

### Post by %hMa@?b&lt;C on 2007-07-24
> **Al3xK3aton said:**
> That guide doesn't say how to mod a CD burner to burn/play DVDs. Any advice?

that is not what it is for.  This is if your DVD burner wont burn dvds under linux, but will burn CDs.  The title should be clear enough. Sorry if i misled you.

---

