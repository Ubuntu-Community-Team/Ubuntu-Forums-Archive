---
title: "File Permission help."
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Cufishing on 2005-12-16
Situation; I use dual boot and a shared HDD for my digital darkroom. I use Ubuntu and GIMP, and WinXp and GimpShop also the only place I can print true life photo quality on my printer.

The HDD is not the issue. It is the folder within the HDD that has become problematic. At first I set up the HDD, and file folder, shared it and all was fine. 
I WAS sharing files in and out of this folder, tweaking in Ubuntu, and printing in windoze with no issues. Yesterday I scanned in a pic, tweaked it, and when I went to save it to print from the other side; File not saved, you do not have permission. Ok, so I start looking around. Out of the blue, there is a "No-Go" icon on my shared folder. Not the HDD itself, just the folder. One in the same as where I have 3GB's of already SHARED pictures. :confused:  There are no issues from the windoze side.  So, I need a little help on this.

1. How do I fix it?
2. How do I prevent it from happening again?
3. What could have caused it?

Basically I think I'm asking how to share an already shared file, that has lost its permissions?
When I click under properties, permissions, it is says I no longer have permission. Furthermore, I can create a new folder on the HDD, next to the original folder, and have no issue. BUT, I can only copy from the original shared folder, that then leads to 6GBs of pictures on a 10GB drive, not very efficient.

Sorry about the rant, but 'tis a strange situation indeed.

---

### Post by iansyngin on 2005-12-16
can you login as root in the terminal.
browse to the directory that you are concerned with.
type ls -l and tell me the permissions here.

---

### Post by bscbrit on 2005-12-16
If I understand the situation, you copied some files into the folder under windows, and now cannot access them under Ubuntu.  What kind of format is the drive (FAT/NTFS or whatever).  When you say you are sharing the drive, are you using SAMBA or simply giving both operating systems the use of a shared FAT drive?
But I may have misunderstood, can you please clarify?

---

### Post by Cufishing on 2005-12-16
can you login as root in the terminal.

Not sure. I was under the impression Ubuntu was a sudo, and therefore had no true 'root' user. How do I?

Also, all blockeds are checked, but grayed out and says 'you are not the owner'.
_________________________________

But I may have misunderstood, can you please clarify?

HDD is Fat32, no issue. Shared, as in I had shared it from winxp. In Ubuntu I had it mounted, and permission's granted for read, write etc.
For a couple weeks, everything was fine. Then, just one day, I can no longer save files to, or delete files from this folder. 

____________________________________
Blog type explanation:
Monday, scan picture from hard file into Gimp. Tweak file, save into folder as readyforprint.jpg ~ Reboot to winxp, open print manager, select file readyforprint.jpg, click send to photo printer, receive picture from printer. Enjoy day.

Wednesday, scan picture from hard file into Gimp. Tweak file, save into folder as beachforprint.jpg, "File not saved, you do not have permission to save files into this folder". 

Okay, for the last weeks I did, now yesterday I can't? Also, there is now a little red icon circle with the line through it, on that folder. Not the entire drive, not all of the folders, just the main folder where all of my pictures are archieved. Strangely, I can make new folders, delete those folders, etc. But I can no longer use the main folder as it was designed. I can use files from that folder in a program, but I cannot directly use the file. As in, I can no longer just open that folder and browse it. I can only view it from within a program, like Gimp, or picture viewer etc.

---

