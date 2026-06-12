---
title: "Ubuntu and HFS+"
date: 2007-04-27
forum: Apple Intel Users
---

### Post by drev on 2007-04-27
I have a hard drive from my old WinXP machine that's formatted with the NTFS file system.  I want to take this hard drive and use it for a mac.  I tried running the OS X install disc and using the Disk Utilities to format the drive.  However, it wouldn't let me format the HD.

My question is, can the Ubuntu installer format a hard drive using Mac's HFS+ file system?

(I would check for myself, but I don't have access to a Live CD right now)

---

### Post by phidia on 2007-04-27
I believe the answer is no. I use macs and linux on pcs and macs. hfs+ needs to be compiled into the kernel to get r/w although linux will generally read hfs+ You can look at the man pages for mkfs but AFAIK you can't format a drive hfs+ in linux.

---

### Post by drev on 2007-04-27
Do you know of a good utility, then, that would allow me to do it in Windows?

Or do you know another way?

Thanks

---

### Post by ronocdh on 2007-04-27
> **phidia said:**
> I believe the answer is no. I use macs and linux on pcs and macs. hfs+ needs to be compiled into the kernel to get r/w although linux will generally read hfs+ You can look at the man pages for mkfs but AFAIK you can't format a drive hfs+ in linux.
Correct. R/w capabilities for HFS+ and NTFS are not built-in on the Linux kernel; it's possible to add them and recompile, but their performance isn't stellar (though your mileage may vary, of course).

What is the error message you're getting when trying to wipe the disk from NTFS? Another option is to reformat the drive as FAT32 (in Windows) and then reformat (in OS X) to HFS+. That should work nicely.

---

### Post by Enderend on 2007-05-01
Here's one way to handle it.  Go get the [System Rescue CD]("http://www.sysresccd.org/Download").  Burn the image to a CD, connect your hard drive to the computer, and restart to boot to the CD.  When you get to your first prompt type:

fb1024

This will set the screen resolution to 1024x768.  Follow the onscreen prompts to choose your keyboard layout.  When you reach the next prompt type:

run_qtparted

This will run QTParted which is a clone of partition magic.  Using the navigation on the left, browse to your harddrive (the one you connected, not the one where the OS is installed).  Delete any and all partitions.  Save changes.  This will turn your drive into free space.  Where you go from there depends on what you want to do.  

To format as HFS+ (OS X can read), restart the computer and use the disk tool in OS X.  

To format as FAT32 (OS X, Windows, Linux can read) you can stay in QTParted and use the "New" button to create a parition.  

To format as ext3 (Linux can read) stay in QTParted as well or reboot to Ubuntu.  

Hope this helps.

---

### Post by drev on 2007-05-01
I found a way to get the OS X disk utility to recognize the drives.

I physically jumpered the hard drives to be Master and Slave, instead of both being cable select.

Doing this allowed me to format and partition the hard drives in the OS X disk utility without having to otherwise mess with the file systems.

Thanks anyway, for your help!

---

### Post by ronocdh on 2007-05-01
> **Enderend said:**
> Here's one way to handle it.  Go get the [System Rescue CD]("http://www.sysresccd.org/Download").  Burn the image to a CD, connect your hard drive to the computer, and restart to boot to the CD.  When you get to your first prompt type:

fb1024

This will set the screen resolution to 1024x768.  Follow the onscreen prompts to choose your keyboard layout.  When you reach the next prompt type:

run_qtparted

This will run QTParted which is a clone of partition magic.  Using the navigation on the left, browse to your harddrive (the one you connected, not the one where the OS is installed).  Delete any and all partitions.  Save changes.  This will turn your drive into free space.  Where you go from there depends on what you want to do.  

To format as HFS+ (OS X can read), restart the computer and use the disk tool in OS X.  

To format as FAT32 (OS X, Windows, Linux can read) you can stay in QTParted and use the "New" button to create a parition.  

To format as ext3 (Linux can read) stay in QTParted as well or reboot to Ubuntu.  

Hope this helps.
Very informative post and I hope it helps out drev. But I just want to add that in the final review of options, where you list out HFS+, FAT32, and ext3, the *write* capabilities of the file systems should be noted. Thus:
[LIST]
[*]HFS+: read/write capability in OS X, read capability in Linux, nothing in Windows (haven't found a free solution; someone post if you know of one!)
[*]FAT32: read/write capability on all three OSes! Limitations on file size and file metadata, however.
[*]ext3: read/write in Linux (native format); installable filesystems (open source) are available for both OS X and Win XP. I personally use IFS for both and thus I can read/write to all my drives in all three OSes. So formatting to ext3 for external drives is more beneficial to me than using FAT32, which has limitations.
[/LIST]

For more information, check out the [Wikipedia article]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") on filesystems; all FSes are linkable, so you can drill down and read about each in depth. Also, the IFS I mentioned can be found [here]("http://www.fs-driver.org/") for Windows XP and [here]("http://sourceforge.net/projects/ext2fsx/") for OS X.

Hope that helps!

---

### Post by Gen2ly on 2007-05-02
Don't forget my HOWTO!  :)

[HowTO HFSplus in Linux]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494")

---

