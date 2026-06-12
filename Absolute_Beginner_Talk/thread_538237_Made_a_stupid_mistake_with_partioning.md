---
title: "Made a stupid mistake with partioning"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Frodaddy on 2007-08-29
So I have Win XP and im trying to do a dual-boot via this guide:
[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

I created a Ubuntu CD and started messing around with Ubuntu. Began the install process and was at the partition screen. I have two hard disks C and G. I went to do the auto partition option (that ubuntu auto selects) on my hard disk G. This disk mainly stores my mp3's, etc. I thought the partitioning agent would just chop off a section for a partition that contained free space but I'm pretty sure it didnt. I recieved an error saying something about Windows Disk Manager was responsible for that disk and it couldnt complete the task.

Now when i run windows i try to open my G drive and its asking me to format the drive...I'm assuming that I've now corrupted my disk and need to whipe it clean again, but I want to be sure that before i do this that i cant retreive all of the data i had on their previously. None of the programs contained int her work anymore (duh). Can anyone confirm that this would most likely need to be re-formatted or is there still hope to retrieve anything that was on there?

Also, now moving forward do i need to created a partition via Windows and then goto Ubuntu and install on this new partitioned drive?

Appreciate the help in advanced.

Regards,
Fro

---

### Post by logos34 on 2007-08-29
> **Frodaddy said:**
> do i need to created a partition via Windows and then goto Ubuntu and install on this new partitioned drive?

no, you can do it from the livecd using Gparted.

If you can't mount G: from the live cd to access your files (and you probably can't because something went terribly wrong during the resizing), try running chkdisk/error checking with repair option in windows.  Not sure it will help even if you can.

Look around for some free disk data recovery programs before you give up and wipe it.

---

### Post by Frodaddy on 2007-08-29
Ya thanks for the quick reply! I

I just re-ran ubunutu via the LiveCD and mounted the G drive and all of the files are still in tact. Just in case i moved some files from one disk to another, however i have some program files which id like to keep. im going to see if i can run some recovery since i think all of the files are in tact but windows just doesnt recognize it as a formatted drive.

If anyone has any other suggestions or insight please let me know. Thanks!

EDIT: just tried chkdsk and its telling my that drive G is a RAW format. gparted tells me its NTFS tho...weird

---

### Post by Frodaddy on 2007-08-29
Quick update:

I found this tool:
[http://www.z-a-recovery.com/unformat-tutorial.htm](http://www.z-a-recovery.com/unformat-tutorial.htm)

Im running it now and hopefully i can recover my files. Again, if anyone has any other ideas let me know.

Thanks,

-fro

---

### Post by logos34 on 2007-08-30
> **Frodaddy said:**
> just re-ran ubunutu via the LiveCD and mounted the G drive and all of the files are still in tact. Just in case i moved some files from one disk to another, however i have some program files which id like to keep. im going to see if i can run some recovery since i think all of the files are in tact but windows just doesnt recognize it as a formatted drive.

...

EDIT: just tried chkdsk and its telling my that drive G is a RAW format. gparted tells me its NTFS tho...weird

Hmm...I didn't think you had much of a chance of accessing those files if windows no longer recognizes its own filesystem...weird is right...stranger things have happened though.

---

