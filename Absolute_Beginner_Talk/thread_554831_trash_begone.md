---
title: "trash begone"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by pnotequalsnp on 2007-09-19
I have a couple of other drives that are used for storage but when I delete something, it does not show up in the trash.  Only things that I delete in the root file system show up in the trash.  Also, when I delete them (from the other drives), it does not reflect the free space I have created.

---

### Post by quixotic-cynic on 2007-09-19
> **pnotequalsnp said:**
> Also, when I delete them (from the other drives), it does not reflect the free space I have created.

This suggests that it is being directed to a trash folder and not completely deleted. You can use shift-delete to avoid having stuff sent to the trash. To empty the trash on the devices look for a *.Trash-1000* or simmilar folder (it will be hidden by default - you need to be viewing hidden files - often Ctrl-H) and delete any files in the .Trash/files and .Trash/info subdirecotires.

---

### Post by spd106 on 2007-09-19
If you go to the View menu in Nautilus and click Show Hidden Files, you should see a folder in the mounted file systems root directory called Trash-'username'. This is where your files are moved to rather than deleted permanently. You can hold shift and press delete to bypass this.

---

