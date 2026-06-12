---
title: "Recycle Bin?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-09-29
Hello all,
I've backed up a bunch of files to a drive on my system. I had a second drive, which I formatted. Its primary partition is mounted at /Share. Next, I copied my group of files across. Then, I deleted the originals. However, there is no indication that the files were REALLY removed. Is there some sort of recycle bin in Linux or something, because I'm not seeing any space freed up on the drive.

---

### Post by morphodone on 2006-09-29
There is a trashcan...

It's located on the very right bottom of my screen.  In the taskbar.

---

### Post by bulldog on 2006-09-29
Yep,Ubuntu has a trash can :D 

Look in your home folder and set show hidden folders on.

Look for a folder named .Trash and see what's in it.

Should be an Icon somewhere on your desktop too :D

---

### Post by JoshHendo on 2006-09-29
If you backed up a drive, but deleted files are taking up space, those files are still there.

Press Ctrl-H to show hidden files. Look for .Trash-<username>. Click on it and then press Shift-Delete. You will then be asked if you want to premanently delete everything, select Delete.

Hope this helps :)

- Josh

---

### Post by gantww on 2006-09-29
Ah. That got rid of them. Many thanks.

---

