---
title: "moving files taking FOREVER"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by pantsroptional on 2007-03-09
I recently installed the ntfs-3g driver so that I could make my second hdd dedicated to just holding my personal data, and eventually dual boot with windows on a third hdd. During the reformat (it used to be ext3) I moved all my stuff off of that second drive. I put half of it on the drive with Ubuntu on it, the first drive (which is ext3), and the other half on an external USB drive (ext2). 

After formatting the second hdd, reading files off the USB and writing them to the second NTFS drive is taking FOREVER. It's been moving a 7GB folder for over 48 hours IN THE FOREGROUND!

I did a test; I moved a single album folder from USB to the second drive. It took over an hour. I moved the same folder from the first drive to the second drive. It took about 10 minutes. For each time, I made sure that no other processes were taking up CPU time. I'm unhappy about both results but the first time is totally outrageous! The folder was about 80MB! My machine isn't a 486! I have a 1.8Ghz with 768MB SDRAM and the USB is 2.0. What's the deal!?

I don't remember the time it took to initially move the stuff off of the second partition before formatting taking a noticable amount of time.. and the drive sounds quiet, I don't think it's about to die. The only thing that has changed since then is the second drive is now NTFS running on the most recent version of the ntfs-3g version. I also upgraded to Edgy in between changing the disk from ext3 to NTFS. HELP!

---

### Post by userundefine on 2007-03-12
NTFS writing is still very experimental and while it is improving it is by no means foolproof.  And I'm not surprised to find that a simple [Google search]("http://www.google.com/search?hl=en&q=ntfs-3g+slow&btnG=Search") brings up a ton of hits.  Use a better filesystem or you'll have to deal with it.  If your concern is reading files in Windows, afaik you can install ext3 support on Windows.  Someone else can elaborate more than I can on that.

---

### Post by dmizer on 2007-03-12
> **userundefine said:**
> NTFS writing is still very experimental and while it is improving it is by no means foolproof.  And I'm not surprised to find that a simple [Google search]("http://www.google.com/search?hl=en&q=ntfs-3g+slow&btnG=Search") brings up a ton of hits.  Use a better filesystem or you'll have to deal with it.  If your concern is reading files in Windows, afaik you can install ext3 support on Windows.  Someone else can elaborate more than I can on that.
indeed there is.  this will be significantly more accessible than ntfs write support in linux.
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

