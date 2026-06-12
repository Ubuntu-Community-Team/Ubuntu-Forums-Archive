---
title: "Linux recognizing IAUDIO X5L as &quot;read-only filesystem&quot;"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-08-16
I've been a happy Ubuntu user for nearly a year now, and I've never had any problems using my IAUDIO X5L mp3/etc. player in linux.  Until recently.  I recently deleted all of the music, and then transferred a bunch of new files to the player's hard disk.  During the process, gnome froze up a bit, and I had to manually disconnect the player from the computer.  No apparent problems here, I still had the music on my device and it all plays fine.

However, now when I attempt to access the music, it claims that the device is a Read-Only Filesystem.  I tried chmod and chown (and their gui equivalents in gnome) to no effect (it won't change the permissions, even when logged in as root).  I can write to the device from my windows xp installation, but unfortunately the bulk of my music collection is on an ext3 formatted external drive.  But in Ubuntu (and in a brand-new Linux Mint installation on another partition), I can't do anything.  I'm at a complete loss, as I feel like I've tried everything here, and I've never had this problem before.

Also perhaps of note, there is one file on the device that contains zero bytes but is somehow corrupt and can't be deleted.

Thanks for any help!

[wickstopher]

---

### Post by wickstopher on 2007-08-16
PROBELM SOLVED.

It turns out, the problem had something to do with the corrupt file on the device.  I tried deleting it in both Linux and Windows, to no avail.  For some reason they couldn't deal with it.  But, in USB host mode on the X5L, you can delete files on the drive, and it allowed me to delete the file from there.  Since deleting the file, the device has been back on good behavior.  Whew!

---

### Post by wickstopher on 2007-08-17
I take that back.  The problem seemed to have gone away.  But it is back again and in full force, and now I can't seem to identify the culprit.  Not only is Linux seeing the device as a Read-Only filesystem, it is not correctly showing the amount of disk space left on the device.  When I open up the filesystem on my computer it says that I only have 1.4GB of space remaining (the amount I had left before deleting files).  When I browse in USB Host mode on the device, all of the free space shows up (28378MB).  Is it safe to reformat the device with gparted and reinstall the firmware?  Or can anyone think of a solution for this problem?  I hope I'm wording this clearly enough, as it is a very strange problem.  Thanks for any help!

---

### Post by wickstopher on 2007-08-17
I reformatted the device in Windows using JetShell (cowon's software for the device).  I am no longer having the Read-Only problem, but for some reason linux still doesn't free up the space when I delete files from the device.  Anybody know what the problem is here?  The file system is fat32.  could that have anything to do with it?  I never had any problems  of the sort with my external hard drive which is also fat32.  The only way I get the space back is if I manually rm the files from the command line.  Not even if I delete the files straight from the device.  The device shows that the space is available, but linux does not.    Thanks for any help!

---

### Post by squig on 2007-11-14
Did you make any progress on this? I have the exact same problem with my U3, can't delete any files from the device after accidental removal without unmounting.

I installed cowon's JetShell PRO using WINE, but I cannot reformat the device or delete files, even using JetShell. :(

Is there a down-and-dirty way to wipe the drive using the command line, then reformat using JetShell? I have no idea what to try.

Thanks.

---

### Post by wickstopher on 2007-11-14
Unfortunately, I have not been able to get JetShell in WINE to access the device.  The program works, but it doesn't recognize that the device is plugged in.  Somebody else out there may have some insight into this, but I can't get it to work.  Not a big deal, though, as it's fairly simple to drag and drop, and Amarok actually has some functionality transferring files to the device straight from the GUI (although you will have to go back into the filesystem of the player and move the files into the MUSIC directory...hopefully they have this improved when Amarok 2 comes out).

Anyhow, I digress.  There ended up being a corrupt file that I couldn't get rid of, even via the command line, so unfortunately what I had to do was install JetShell on my WinXP partition and reformat the device from there.  That's the only advice I can offer on the matter.  If you don't have access to XP at home, I'm sure you can find someone out there who would be willing to take 30 minutes and let you install JetShell and reformat the device.  JetShell will wipe the drive for you, so you don't have to worry about that.  Good luck!  And just make sure from now on to safely unmount the device prior to disconnecting.  I didn't initially, and got warning messages every time.  I ignored them for months, and then the one time it mattered, I ended up having to go through all this to get my device back!  Hope this answers your question.

---

