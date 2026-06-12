---
title: "[SOLVED] OS X showing HFS, Ubuntu showing HFS+?"
date: 2008-07-05
forum: Apple Hardware Users
---

### Post by nkri on 2008-07-05
Hey, everyone, I'm really confused:(.  I bought an external hard drive and formatted to HFS+ because I use it for all my photo stuff in OS X, but when I found out that you can't write to HFS+ in Ubuntu, I simply turned off journaling with the Apple terminal:
```
diskutil disableJournal /dev/disk2s3
```

This seemed fine, but when I looked at it in Ubuntu, it showed HFS+ even though I disabled journaling.  What the heck is going on????

This is really annoying since I've been trying to use PartImage to backup my internal HDD onto the external, but it won't let me (saying that it is an incompatible format and try again, even though HFS is supported).  What should I do??

Thanks!
-nkri

---

### Post by DGortze380 on 2008-07-05
I believe disabling journaling is temporary and only works while mounted in os x. try mounting the external, disable journaling, unmount, remount, check format in disk utility. I bet it comes up hfs+ (journaled).

I think you'll need to reformat the external as HFS not journaled.

---

### Post by nkri on 2008-07-05
Yeah, that's what I feared, but thanks for clearing it up for me!
-nkri

---

### Post by flaggh on 2008-07-05
> **DGortze380 said:**
> I believe disabling journaling is temporary and only works while mounted in os x. try mounting the external, disable journaling, unmount, remount, check format in disk utility. I bet it comes up hfs+ (journaled).

I think you'll need to reformat the external as HFS not journaled.

I don't believe this is accurate.  HFS+ non-journaled is not the same thing as HFS.  When you disable journaling, it will still be an HFS+ formatted drive.  HFS is a different filesystem.

---

### Post by nkri on 2008-07-06
Yep, I discovered that right after my second post.  HFS+ is Mac OS Extended (available in OS X), while HFS is Mac OS Standard (used in OS 9 but not available in OS X).  Journaling has nothing to do with it, so I'm assuming I would have to re-format with GParted, right?  Disk utility doesn't do HFS:mad:.

Thanks!
-nkri

---

### Post by DonnieP on 2008-07-06
> **flaggh said:**
> I don't believe this is accurate.  HFS+ non-journaled is not the same thing as HFS.  When you disable journaling, it will still be an HFS+ formatted drive.  HFS is a different filesystem.
I have been needing to write to my OSX partition from my Ubuntu partition (on the same drive), so I tried disabling journaling on this internal drive.  This worked - it wasn't just temporary - which I confirmed by rebooting into OSX.  And it's still HFS+.  However, when I tried to disable journaling on my HFS+ external drive (used for Time Machine), disk utility squawked and refused to go there.

---

### Post by nkri on 2008-07-06
> **DonnieP said:**
> I have been needing to write to my OSX partition from my Ubuntu partition (on the same drive), so I tried disabling journaling on this internal drive.  This worked - it wasn't just temporary - which I confirmed by rebooting into OSX.  And it's still HFS+.  However, when I tried to disable journaling on my HFS+ external drive (used for Time Machine), disk utility squawked and refused to go there.

By "squawked and refused to go there," do you mean that you couldn't disable journaling using the button in disk utility?  If so, all you have to do is press Option+File.  "Disable Journaling" will show up in the menu.  Or, if you want to use the terminal:
```
diskutil list
```
to find out the name of the disk, and
```
diskutil disableJournal /dev/*Volumename*
```
to disable journaling on the disk.

Good luck!
-nkri

---

### Post by DonnieP on 2008-07-06
> **nkri said:**
> By "squawked and refused to go there," do you mean that you couldn't disable journaling using the button in disk utility?  If so, all you have to do is press Option+File.  "Disable Journaling" will show up in the menu.  
I did Option+File (which is what I did successfully to disable journaling on the internal hard disk).  On the external drive, after selecting Disable Journaling from the menu, it gave me some error message to the effect that it couldn't disable journaling on this drive.  Same message repeated after reboot on another try.

---

### Post by nkri on 2008-07-06
Oh, that probably has something to do with Time Machine (I'm not sure, as I still use Tiger and don't have this feature:().

---

### Post by amarkitanis on 2008-07-24
sorry to bring up this thread again, 

if you have an HFS+ journaled external hard disk and you read/write files in Ubuntu, does that hard disk become corrupted under mac os x?

I've been using my external hard disk (HFS+ journaled) both on linux, and windows (using MacDrive) both reading and writing. 

I haven't had used the extenal disk with mac for a while. 

Doing this today, the hard disk does not mount, and under disk utility it says that the file system is fat 32 and it cannot be mounted nor repaired. 
Linux and Windows Vista can read files and write to the hard disk perfectly fine. 

Gparted recognises the disk and says that its filesystem is  unknown. 

Any suggestions anyone?

Thanks

---

### Post by cyberdork33 on 2008-07-25
*oops

---

### Post by cyberdork33 on 2008-07-25
Please do not double post:
[http://ubuntuforums.org/showthread.php?t=869655](http://ubuntuforums.org/showthread.php?t=869655)

---

