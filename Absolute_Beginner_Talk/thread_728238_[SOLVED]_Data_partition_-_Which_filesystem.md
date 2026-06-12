---
title: "[SOLVED] Data partition - Which filesystem?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-03-18
I'm tying up some loose ends after a bit of a system change-around.

I have an 80 gig data partition currently available to me, that is about 50% full with assorted music and video etc. It is an NTFS partition from my ex-windows installation and it is auto mounted by Ubuntu (7.10), and I am fully able to access the data on it.

Questions:
1)
Is this safe data wise? Reading from and writing to an NTFS partition? Iv had no trouble thus far, but for the most part Iv been using the video and music files from it, rather than writing to it.

2)
Assuming it IS safe, is there any benefit to be gained from formating it to ext3? The data on there will never be used by Windows again (Ill not be going back), but if its safe to use the drive as it is, unless I'm going to get some clear benefit from it, I see no reason to change anything.

Thanks for any pointers you can give

Max

---

### Post by forrestcupp on 2008-03-18
It's safe.  But if you're absolutely sure you'll never use Windows again, you may consider going to ext3.  It seems like ext3 is a little faster in Linux, and it's definitely more efficient.

---

### Post by Oldsoldier2003 on 2008-03-18
> **MaxVK said:**
> I'm tying up some loose ends after a bit of a system change-around.

I have an 80 gig data partition currently available to me, that is about 50% full with assorted music and video etc. It is an NTFS partition from my ex-windows installation and it is auto mounted by Ubuntu (7.10), and I am fully able to access the data on it.

Questions:
1)
Is this safe data wise? Reading from and writing to an NTFS partition? Iv had no trouble thus far, but for the most part Iv been using the video and music files from it, rather than writing to it.

2)
Assuming it IS safe, is there any benefit to be gained from formating it to ext3? The data on there will never be used by Windows again (Ill not be going back), but if its safe to use the drive as it is, unless I'm going to get some clear benefit from it, I see no reason to change anything.

Thanks for any pointers you can give

Max

formatting it to ext3 does some good things for you
1. it won't need defragging
2. permissions will be properly set on the files
3. you wont need to run non linux FS modules
4. its just cooler to be Microsoft Free :)

---

### Post by MaxVK on 2008-03-18
Thanks for your comments. I think I might as well change to ext3 then, since Ill not be going back to Windows now.

Questions:
1)
How to I format the drive? I just had a (quick) peek around but I cant see anything that looks like it is a disk formatter (The only one Iv seen is in the live CD).

2)
Once the drive is formatted how do I make it auto mount and appear on the desktop, which is what it does now?

Regards

Max

---

### Post by Arthur Archnix on 2008-03-18
This thread might give you some ideas: [http://ubuntuforums.org/showthread.php?t=334795](http://ubuntuforums.org/showthread.php?t=334795)

Also, consider typing man mke2fs in a terminal.

Generally anything mounted under /media or /mount gets put on the desktop. You'll need to edit your fstab file and create a directory for it. Again, man fstab is a good place to start.

---

### Post by ajgreeny on 2008-03-18
You will need to backup the files on the partition first, then use the live CD partition editor (gparted) to delete the partition and make a new ext3 one.  I can't remember if you can do it in one action, ie, just format as ext3 without deleting first, but you could try that, and if it doesn't work, just delete first, then make new.

Once you have the partition, you will need to add it to your /etc/fstab file with a line as follows:-
/dev/hdb1       /media/data   ext3    defaults  0  1

The /dev/hdb1 will probably be different in your system so you will need to get that first, and the mount point can be wherever you want, just make sure you mkdir of the chosen named point before you reboot or you will get an error at boot up.  You will also, I think, need to chown to your user name or perhaps to all users.  Can't remember the exact command for that but if needed I think you can do it with ```
gksudo nautilus
``` and chose properties from the right click menu for that mount point.

---

### Post by MaxVK on 2008-03-19
Thanks guys, its sorted now.

Regards

Max

---

