---
title: "Missing mail when trying to share Thunderbird mail between Windows &amp; Ubuntu"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by roopak on 2007-11-19
Hi, I am dual booting my computer between windows and ubuntu and am trying to share thunderbird mail between both opertating systems.

I am able to see all the mail and folders in windows without a problem.  The issue arises when trying to see the mail folders in ubuntu.

I have a shared thunderbird profile in a shared FAT32 partition.  Copied my windows profile to it and modified the prefs.js file in ubuntu to reference the new location of the profile folder.  I then also removed the lines in the prefs.js file which contain “....[ProfD]....”.

I then started thunderbird and all my mail was there. I was very happy.

The problem is that when I try to open thunderbird again I can only see the main folders “Gmail” and “Local Folders” but can´t see or open any of the sub-folders.  Hence can´t see any mail.

If I go back to prefs.js and remove the lines which contain “....[ProfD]....”, Save prefs.js and run thunderbird again I can then see all my mail. 

 If I then restart thunderbird all the mail sub-folders are missing again.

Can someone please help.

Thanks.:)

---

### Post by Arthur Archnix on 2007-11-20
Instead of manually editing the file, why not just run 
```
thunderbird -P
```
Then create a new profile, point it at your shared folder.

---

