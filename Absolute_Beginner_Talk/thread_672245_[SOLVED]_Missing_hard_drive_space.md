---
title: "[SOLVED] Missing hard drive space"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Terry N on 2008-01-19
Hello,
I accidental captured video in the root folder. The only way I found I could remove it was to use gksudo nautilus. I moved the items to the trash although they never showed up ad being in there so I thought because they were so big they were just deleted. I did click on empty trash. The file system properties showed it did not free up any space on my hard drive. I did check the Nautilus trash and nothing was in there. I checked the trash in a terminal and found stuff in there so I ran the command in the terminal to empty it and the items were removed but still no more free space. I cannot find a root trash folder. The only subdirectory under root is Desktop. 

Thank you for any help.

Terry N

---

### Post by forestpixie on 2008-01-19
do gksudo nautilus again and look in home after enabling view hidden files

---

### Post by nick_h on 2008-01-19
Try:
```
sudo ls -al /root/.Trash
```
This is where you would expect to see the deleted files.

---

### Post by mister_pink on 2008-01-19
If you still can't find where they've gone you could try using the disc usage analyser (in Accessories) to see if you can spot some large files somewhere weird.

---

### Post by Terry N on 2008-01-19
Hello,
Thanks for the reply. I did find the files after running gksudo nautilus and clicking show hidden. They are in the root/trash folder. Before i go any farther can you tell me how to remove them?

Thanks Terry

---

### Post by gerscht on 2008-01-19
You can delete files in nautilus with
```
shift+delete
```
(instead of moving them to .Trash)

---

### Post by Terry N on 2008-01-19
Thank you for all the help!!!!

shift-delete in gksudo nautilus did the trick.

---

