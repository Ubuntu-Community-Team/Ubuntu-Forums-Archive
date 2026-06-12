---
title: "How to bypass/configure the trashcan"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Crakie on 2007-03-27
I have my data files on FAT32 partitions. When I delete them, they are put in the trashcan, which located on the partition / is on. In other words, when deleting a large file, this operation takes quite long because it is essentially copied between two partitions. 

Several options to solve this are acceptable to me. I could bypass the trashcan altogether, for example. Or I might be able to set up a separate trashcan on every partition, so copying would not be required anymore. Any ideas on how to do that? (All suggestions welcome, of course)

---

### Post by NikoC on 2007-03-27
In a terminal doesn't:

sudo rm -r directory_name

delete a dir without copying it to trashcan?

---

### Post by AtrejuT on 2007-03-27
in nautilus - preferences - behaviour you can add an entry to the context menu allowing you to bypass the trash.

---

### Post by asimonelli on 2007-03-27
You can also press and hold the Shift key and press delete with the file selected.  It will prompt you to confirm permanently deleting the file.  

For this situation, it's ideal because you don't want the copy into your trash can, but be careful when permanently deleting files because once it's gone, it's gone.

it's good to make an alias in your .bashrc file to run rm as rm -i so it prompts you whether to delete or not in the terminal.

---

