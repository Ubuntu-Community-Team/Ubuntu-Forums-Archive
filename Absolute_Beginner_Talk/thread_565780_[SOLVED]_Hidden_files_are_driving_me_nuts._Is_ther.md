---
title: "[SOLVED] Hidden files are driving me nuts. Is there anyway to turn this feature off"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-02
My usb pen drive was full of trash files that were hidden and one was locked. so I thought there was space on there.

So had to sudo nautilus to delete these .trash folders. Nightmare

---

### Post by kerry_s on 2007-10-02
in nautilus view.

---

### Post by mysticmatrix on 2007-10-02
ctrl + H in file manager

---

### Post by philinux on 2007-10-02
I mean to always view hidden files, without having to remember to view hidden files.

Edit} when I delete files on my pen dirve it sticks them in a hidden trash folder on MY pen drive. Annoying or what

---

### Post by rhodry on 2007-10-02
If you want to see hidden files all the time by default, simply open a Nautilus folder, go to Edit-->Preferences and on the first tab that appears (Views) there is an option for "Show hidden and backup files". Just turn it on.

Whilst you are there, go to the 2nd tab (Behaviour) and there is an option to "Include a Delete command that bypasses Garbage Bin". Turn that on as well.

With this on, you can delete files without them going to the Garbage Bin - do be aware you CANNOT get them back with this option on if you make a mistake. You can then delete a file by right clicking on it (or them) in Nautilus and your pop up will include two options:
"Move to Garbage Bin", and 
"Delete"

Also, holding the Shift Key while pressing Delete Key will bypass Garbage Bin.

I may be wrong, but, I thought that mounted external usb drives that share your permissions share a common desktop garbage bin. That is, if you delete a file on the external drive that you own, it goes in your desktop garbage bin. So, if you just empty your desktop garbage bin then any files in the garbage bin on the external drive were gone. Hmmm, I will have to test that out.

Cheers,
Rhodry.

---

### Post by nowshining on 2007-10-02
nope pen drives or  flash drivers  share there own .trash folder, so does NTFS HardDrives.

---

### Post by rhodry on 2007-10-03
> **nowshining said:**
> nope pen drives or  flash drivers  share there own .trash folder, so does NTFS HardDrives.

Well, I know nothing about pen & flash drives as I do not use them. However, I can confirm; and I have just tested to check my memory, I have used & continue to use a variety of external usb hard drives and my understanding of the Trash Bin is correct there.

All deleted files from all mounted ext3 hard drives owned by the current user login will be in the Trash Bin that appears on the desktop/panel of that user. eg. On one external drive I use for backups there are a number of folders from different logins on my main machine, say Mickey & Donald & Goofy. If Mickey is logged in and deletes file1 in /home/Mickey it goes in the /home/Mickey/.Trash folder. If Mickey then goes to /media/disk (the external drive) and deletes file2, it goes in /media/disk/.Trash-Mickey on the external drive. Even though the two deleted files are physically on seperate hard drives, if Mickey opens the Trash Bin icon on his desktop/panel, both files will be there and both files will be expunged if he Empties the trash bin.

The external drive has its own .Trash folders, but it appears to be the file ownership that determines whether or not you can clear them from your desktop/panel icon. I can't see why a pen drive would be different so long as it is mounted and files are owned by the current user logged in on the desktop. Makes sense to me :)

Cheers,
Rhodry

---

### Post by philinux on 2007-10-03
> **rhodry said:**
> If you want to see hidden files all the time by default, simply open a Nautilus folder, go to Edit-->Preferences and on the first tab that appears (Views) there is an option for "Show hidden and backup files". Just turn it on.

Whilst you are there, go to the 2nd tab (Behaviour) and there is an option to "Include a Delete command that bypasses Garbage Bin". Turn that on as well.

Cheers,
Rhodry.

Many thanks for this and I now also found out why nautilus default show my home drive as 10meg while konqueror showed it correct as circa 750meg see attached. The default for preview folders is local files only. This needs to be set to "Count number of items - ALWAYS"
That was very annoying default behaviour.

---

### Post by nowshining on 2007-10-03
hmm on my Internal Extra Hardrive - 2nd - it has it's own .trash even If I delete it however It does go into my desktop trash, again it's NTFS so that's probably why, ext3 and permissions - that one u said determine where they go, great We both learned some info. here. :)

---

### Post by nowshining on 2007-10-03
> **philinux said:**
> Many thanks for this and I now also found out why nautilus default show my home drive as 10meg while konqueror showed it correct as circa 750meg see attached. The default for preview folders is local files only. This needs to be set to "Count number of items - ALWAYS"
That was very annoying default behaviour.


lolz I saw ur last thread, :) great thanks for that info. it helped me learn something also. :P didn't know that and now I do.

---

### Post by philinux on 2007-10-03
Yep I know i been using konqueror for this reason.

I was backing up my home folder to the pendrive but needed to know exactly how big it was. :lolflag:

This had me flumuxxed,.

---

### Post by nowshining on 2007-10-03
lolz, how huge is ur pen drive, Mine is 1gb advertised, but less of course and uses vfat.

---

### Post by philinux on 2007-10-03
4 gig advertised. 3.8 format to ext3. My home folder started out at 3.2 gig. Moved some files,deleted some, compacted TB folders and now 750 meg. Se I'm just about to set up a separate home partition so backup essential. But the system kept putting hidden folders on the pen drive and deleting them to .trash, hidden, on the pen drive. Now its sorted. :)

---

### Post by nowshining on 2007-10-03
WOW, ur lucky - yes it does, those are backups after u save a text file of course.. :) I get those a lot and that's incase something happens to the first, it's automatic, however then auto-removing them to the trash is odd and i've never heard of that before. Compared to windows tho .trash folder is great whereas windows would just delete them. By the way using an ext3 on it will exclude it by defualt from many windows boxes and it will not see it I think. vfat is always the best to use, however I don't think it will go over or even up to 3gigs so ur best bet would of been fat32. :)

---

### Post by philinux on 2007-10-03
Thats may seem ok but when you back up your home folder to a vfat or fat32 system it cannot create any symlinks. cos I kept getting error symlink cannot be create SKIP, SKIP ALL.

So I thought aha must need ext3. Voila. Once I've got partition up I'll partition pendrive and have fat32 and ext3

---

### Post by nowshining on 2007-10-03
oh, :)

---

