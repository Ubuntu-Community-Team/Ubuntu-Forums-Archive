---
title: "Deleted files won't appear in the Trash Can"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Archmage on 2007-01-24
I'm using Edgy and when I'm using nautilus to delete my files files from all but one partition the files will go into the Trash Can - like they are supposed to do.

But when I delete files from one partition that I add manual later (because I got a new harddrive) these file wont show up in the Trash Can. Although I can see the files in the .trash-username-folder.

What can I do so that these files will be also shown in the Trash Can?

Thank you in advance for your answers.

---

### Post by Steve Baker on 2007-01-24
I really don't know the answer here but... :) 

Is it possible that each partition has its own trashcan?  Maybe you're only looking at the trashcan for one partition.  Just a thought.

SEB

---

### Post by Archmage on 2007-01-25
Thank you very much for your input. I'm using the Gnome applet Trash Can. And IMHO this is showing every .Trash-Folder. I even enter *trash::* in nautilus and notice that the delete files stil not there. :( 

I tasted a few partions on my PC - all but one are showing in the Trash Can.

/home ext3 on hda4 - delete files go into /home/username/.Trash-username and will show up in the Trash Can

/data ext3 on hda3 - delete files go into /data/.Trash-username and will show up in the Trash Can

/hd2 xfs on **hdc** - delete files go into /hd2/.Trash-username and will **not** show up in the Trash Can

The differentce that I can see:
- I bought the hd2 later - maybe I need to announce (beside /etc/fstab) this harddrive for the trashcan?
- This one is xfs while the other ones are ext3. But on my other PC this works (/ ext3 on hdb2 and /home xfs on hdb3) but there delete files from /mnt/win ntfs on hda1 wont show up
- I didn't use UUID for /hd2 partition

That is all I can provide. Someone have an idea that I can try?

---

### Post by Archmage on 2007-01-29
I solved the problem.

I just needed to mount the harddrive with UUID and restart.

---

