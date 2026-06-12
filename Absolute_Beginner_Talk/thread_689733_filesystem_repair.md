---
title: "filesystem repair"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-02-06
is there a way to repair a damaged filesystem table?  i have an issue where i can't see any of my files on an ext3 volume.  i used photorec and was able to see the files that i thought i had lost, and it was suggested that this is the result of a damaged filesystem table.  i'm not sure how i should proceed further to restore the files.  any suggestions/solutions would be greatly appreciated.  thanks.

---

### Post by cmnorton on 2008-02-06
What is the file system type?

Here are some useful links:

[http://ubuntuforums.org/showthread.php?t=689190&highlight=fsck](http://ubuntuforums.org/showthread.php?t=689190&highlight=fsck)
[http://ubuntuforums.org/showthread.php?t=316345&highlight=fsck](http://ubuntuforums.org/showthread.php?t=316345&highlight=fsck)
[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

---

### Post by Matt26 on 2008-02-06
it is an ext3 filesystem- would fsck work on this issue?

---

### Post by philinux on 2008-02-06
Yes either from the live cd or from recovery mode.

---

### Post by Matt26 on 2008-02-06
i tried fsck -t ext3 /dev/sdb1 and it came up clean... no mention of any errors.  am i using the command wrong- i have seen a number of suggestions that fsck would fix this issue.

---

### Post by ByteJuggler on 2008-02-06
Where/How did you lose your files?  Were they deleted accidentally?  Alternatively, are you checking the right partition? (Sorry to ask a possibly obvious question, but you never know... :)  )

---

### Post by Matt26 on 2008-02-06
no worries, i completely understand- i say the same thing to my staff at work when computer issues arise :)

the files were lost yesterday after my system froze up just after installing some new OS updates and i had to do a hard reset on the PC- when i logged back into ubuntu i checked the volume and the files were not there- gparted even shows the volume as being empty.  however, photorec shows the files i am looking for when i access the volume.  so i ran fsck but it says the volume is clean.  any ideas?

---

### Post by Matt26 on 2008-02-06
ok, so i'm one step further now- i checked gparted after running fsck and it turns out that it did do something after all- i mounted the volume and there were my files!  so i thought i should be good to go now... i logged back into ubuntu on my PC and unfortunately the volume is still showing nothing, although gparted is still showing the volume with the appropriate amount of space taken up.  would unmounting the volume from here and performing another fsck do any good here?  i have the volume auto-mounting at boot.

---

### Post by Matt26 on 2008-02-06
new development- i rebooted ubuntu with the volume unmounted and when i manually mounted it after logging in, my files are there again!  so i unmounted and performed another fsck on the volume, then rest my fstab file to auto-mount the volume again, rebooted, and the files are gone again!  this is weird... anyone have ideas what might be the issue at this point?  i'm confused by this.

---

### Post by crjackson on 2008-02-06
> **Matt26 said:**
> new development- i rebooted ubuntu with the volume unmounted and when i manually mounted it after logging in, my files are there again!  so i unmounted and performed another fsck on the volume, then rest my fstab file to auto-mount the volume again, rebooted, and the files are gone again!  this is weird... anyone have ideas what might be the issue at this point?  i'm confused by this.


Please turn off the auto-mount again and then back up your files to a safe location.  Then start tinkering from there.  I'm no expert on file systems, but I don't want you to have a data loss.

Once it's all backed up safe and sound, then you can even go radical and reformat the volume if needed.  Right now, I would worry about data safety first.

---

