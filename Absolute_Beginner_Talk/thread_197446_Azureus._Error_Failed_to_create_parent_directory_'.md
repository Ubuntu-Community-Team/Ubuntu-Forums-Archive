---
title: "Azureus. Error: Failed to create parent directory 'opt/azureus/FILE_NAME'"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by corricornpop on 2006-06-15
I have been using azureus fora while now, but one day i went to use it and kept getting this message on everything

"Error: Failed to create parent directory 'opt/azureus/FILE_NAME'"

Why?

---

### Post by ilkerka on 2006-07-12
i am having the same problem.I am trying to download the files on my fat32 partition. I have checked Options->Files->Enable incremental file creation. But still i am having problems. help please..

---

### Post by Sonic Alpha on 2006-07-12
> **corricornpop said:**
> I have been using azureus fora while now, but one day i went to use it and kept getting this message on everything

"Error: Failed to create parent directory 'opt/azureus/FILE_NAME'"

Why?

Is the drive full?

---

### Post by Sonic Alpha on 2006-07-12
> **ilkerka said:**
> i am having the same problem.I am trying to download the files on my fat32 partition. I have checked Options->Files->Enable incremental file creation. But still i am having problems. help please..

Try putting your files on your Linux drive, I believe you only have the option to read the data from a fat32 drive.

---

### Post by ilkerka on 2006-07-12
the funny thing is i fixed that initial problem but now it starts downloading and after 30seconds it says cannot write to disk cannot flush. i guess i ll just have to use my linux drive then transfer it to vfat partition

---

### Post by federicostone on 2006-07-13
Hello,

I've the same issue using Azureus on a vfat partition and I've checked Options->Files->Enable incremental file creation too.
However on an ext3 partition azureus is working without any problem.

please help us

many thanx in advance
Federico from Argentina

--------------Edited-----------------
I solve my problem uninstalling azureus (I was installed azureus using Automatix), and installing the program from the ubuntu's repositories.:D 

brgds
Federico from Argentina

---

### Post by digby on 2006-07-13
If you are getting the message '**Azureus. Error: Failed to create parent directory 'opt/azureus/FILE_NAME'**', the problem is that it is trying to write files in the /opt directory (or subdirectory thereof) that is owned by root.  I had a little trouble with this when trying to update.  

For saving regular files, simply save them to your home folder.  If you're trying to get the updates, open the program by running 'sudo /opt/azureus/azureus'

Make sure to close it and restart the regular way as soon as the update is complete (it's a bad idea to run programs as root that you don't have to). 

The other option is to give yourself ownership of /opt/azureus and it's subdirectories.  A quick search around the forum will tell you all you need to know about doing this w/ the chown command.

---

### Post by anodizer on 2006-08-03
This bug seems to have something to do with capital letters in FAT32. Check the folder azureus is trying to create, it will be something like "CD1". Try to create manually a folder named 'CD1' or 'ASFSFD', hit reload, and you'll see that actually the folder is named "cd1" or "asfsfd'. Really weird.

---

