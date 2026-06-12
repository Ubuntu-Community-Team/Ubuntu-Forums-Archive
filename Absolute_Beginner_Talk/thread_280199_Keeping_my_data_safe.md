---
title: "Keeping my data safe"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by happybill on 2006-10-19
This follows on from my previous thread, Mounting New Partitions.
There are two related queries in this thread - sorry about that.
I use Windows XP and an familiarising myself with Ubuntu.  In XP, all my data files, including the OE6 e-mail store, are kept on a separate partition.  This makes backing up easy.  Also, should I need, or wish, to remove and reinstall XP, the data files remain untouched.  I want to do the same in Ubuntu.
Attempts to follow the advice given in the previous thread were not entirely successful, due to my own incompetence, so I started again.  Ubuntu was installed, alongside XP, with three partitions, root, swap and home.  Having stored some test data files in home, I sought to prove to myself that I could reinstall Ubuntu on newly created root and swap partitions, while keeping the original home partition with its data untouched.  In my case, the installer insisted on reformatting home, I had to delete it and recreate it - thus defeating the object of the exercise.
First Question.  Is it possible to do what I was attempting, if so how?
I thought a possible solution would be to use a FAT32 partition for the data storage, with the additional advantage of access from Windows.  I have already found it is possible to save text files in gedit, and files in OO, to previously created Windows folders in the FAT32 partition, but I would like to be able to copy not only files, but folders and the whole user directory, from home to the FAT32 partition.
Second Question. What is the correct syntax in the cp command to copy the folders and the user directory?  I have tried many variations, but none work and I cannot find any examples either.

All helpful suggestions will be gratefully received.

---

### Post by Sef on 2006-10-19
> Ubuntu was installed, alongside XP, with three partitions, root, swap and home. Having stored some test data files in home, I sought to prove to myself that I could reinstall Ubuntu on newly created root and swap partitions, while keeping the original home partition with its data untouched. In my case, the installer insisted on reformatting home, I had to delete it and recreate it - thus defeating the object of the exercise.
First Question. Is it possible to do what I was attempting, if so how?

I have had the same type of set up (Ubuntu root, home, and swap), and I have been able to just format root and swap, while leaving the home partition alone.

I wonder if you changed the home partition to format. When updating your system, you should leave home.  I delete the root partition and then set it up again.  Next I click on format and all works well.

---

### Post by happybill on 2006-10-19
Thanks sef. I am grateful for the confirmation that what I thought I was doing does work.  It's a great relief.  I don't know what my mistake was, but I must be more careful in future.

---

### Post by happybill on 2006-10-20
Update.

I have found out about <gksudo nautilus>, a command that provides a GUI on which files and folders can be copied by drag-and-drop.  This was on [www.psychocats,net](www.psychocats,net), a very useful site, new to me.  I would still welcome some pointers to a guide about the syntax for commands, cp in particular. All those that I have found seem to be written for (and by?) those exprienced in Unix.

My next task is to get my head round Wine; -what to do with the GUI resulting from the terminal command winecfg.

---

