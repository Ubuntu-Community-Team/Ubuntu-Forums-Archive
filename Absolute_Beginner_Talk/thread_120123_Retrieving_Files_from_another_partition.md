---
title: "Retrieving Files from another partition?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-01-20
Ok, i set up Ubuntu on its own partition, and now have 5 partitions (Ext3, Windows part, Swap, an unused FAT32, and a "free space" thing).  

When i've used live cd's before (such as knoppix), i was able to access my windows files through the linux OS.  However, i've heard of something for ubuntu called a "Shared partition".

I would i go about setting up a partition that can be accessed by both my Linux and Windows os?

---

### Post by Omnios on 2006-01-20
You can mount the fat32 partition and read and write in it from linux.

ubuntu guide link.
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")

---

### Post by dueY on 2006-01-20
Unused FAT partition is what you are looking for.  To mount it in Linux you type ```
sudo mkdir /media/fat32
``` Then ```
sudo gedit /etc/fstab
```
Then add this to your fstab file ```
/dev/sdb6       /media/fat32  vfat    iocharset=utf8,umask=000   0       0
``` but change the sdb6 to wherever your FAT partition is actually located.

Also you can change the folder you make to something else other than "fat32."  Just make sure you stay consistent in the two places it shows up in what I typed out.

---

### Post by Omnios on 2006-01-20
this is your partition = /dev/sdb6  this is the directory you mount it to it can be anything such as ducuements = /media/fat32  this is the file type = vfat

---

### Post by Heretic Monkey on 2006-01-20
Omnios:

Regarding the link you gave, **Example 5.1** describes how to mount a Windows partition manually so that all users can both read and write to the files.  Does this mean that i can access and save files to the windows partition through Ubuntu (on a seperate partition)?

The FAT32 partition is only about 3.5 GB, and i don't really want to go back in and try to resize it (if it's even possible).

*_EDIT_*:  Just a small grievance, but is there anyway to change the terminal labels? There's **"*****@mr348u5982 :~"** in front of the prompt (using random numbers for the example, btw).  I know this is the username and machine name, but do they HAVE to be there, or is there a way to disable them?  I'm the only user on the box, and the titles are just clutering up the screen..... *wow, that sounds really anal...*

---

### Post by Omnios on 2006-01-20
you can read and write fat mounted files ntfs is read only, there is work being done on ntfs to write to ntfs but there is a chance it can corupt your files or even partition. Personaly I have a 50gig winxp drive and a 50gig fat 32 document drive and my linux drive. You could also use the fat drive to tranfer things over when you log into windows.

---

### Post by dueY on 2006-01-20
[QUOTE=Heretic Monkey]Omnios:

Regarding the link you gave, **Example 5.1** describes how to mount a Windows partition manually so that all users can both read and write to the files.  Does this mean that i can access and save files to the windows partition through Ubuntu (on a seperate partition)?][/QUOTE]

You can't (safely) write to a NTFS partition from Linux.  If you want to access AND write(save) files to a Windows partition it has to be FAT32.

---

### Post by Heretic Monkey on 2006-01-21
Thanx Omnios and duey for the help.  I'll just resize the FAT32 partition i have now, or just simply create a new one from the unformatted free-space i have left.

---

