---
title: "Reinstall Feisty and add 2nd hd."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Mt Dew on 2007-07-08
I have decided to put a 20g hd in and add a 2nd 20g hd. The 1st hd is empty and I will use this for the reinstall of Ubuntu.  Both are Fat 32.

The 2nd hd will be used for storage, but it already has some pic/music  files that I want to keep. It actually has a copy of windows that I got the BSOD on and was unable to repair. Can this be done?

Thanks!

---

### Post by logos34 on 2007-07-08
You'll have to format the ubuntu root partition ext3.  If you can read annd write to the fat32 windows partition with your pics and tunes, then you could just leave it that way if you've tried everything you can think of to fix it so it boots.  Personally I'd find a way to transfer that data off and either reinstall windows or at least reformat it to get rid of any filesystem errors, bad blocks, etc.

---

### Post by Mt Dew on 2007-07-08
When I reinstall Feisty will I be able to access the 2nd hd and get rid of the windows and keep the other stuff?
Will Feisty automatically read the 2nd drive?  I am not interested in trying to dual boot with Windows.
Thanks!

---

### Post by logos34 on 2007-07-08
hopefully. linux can access fat32, but you say you got the blue screen of death so maybe there will be problems reading it. dunno.  If you've run filesystem checks/CHKDSK on windows partition and it doesn't help, you could try Testdisk (--> on SystemRescueCD)...Other than that, the best thing to do would be to copy those files off the drive to some DVDs for instance, then reformat the drive (ext3 or fat32) and put the data back on it.

---

### Post by Mt Dew on 2007-07-08
I only have an upgrade XP CD. I had put the drive in a friends computer and it was able to see the files on the hard drive.  In that case will I be able to see them on Feisty? or does that make a difference.

---

