---
title: "Shared Partition Ext3 with XP fs-driver"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by marklid on 2006-08-04
I have been dabbling with Ubuntu for about a week now and want to make the move from XP to Ubuntu, but need to dual boot for a while.

For a shared partition people mentioning formatting it as FAT32 but as I have many files that are over 4GB (DV AVI imports etc.) obviously this would be a problem... I notice that fs-driver enables XP to read and write to Ext3 partitions (I created a small test partition), so my proposal is to have an NTFS partition for the XP install, an Ext3 for / , Ext3 for swap and the rest of the free space as Ext3 for /home - with all my data and personal files being in the /home partition, which would then be shared with XP using fs-driver.

Is there any disadvantage to using this method ?
Would this be a suitable way to share my Thunderbird emails and settings between the two OSs ?
Are the Windows read/writes to Ext3 using fs-driver pretty robust (there is some data I can't really risk getting corrupted) ?

Thanks for any advice, and any thoughts you have on the above.

Cheers,

Mark.

---

### Post by aysiu on 2006-08-04
It should be fine.

Just be careful not to modify from Windows any of the hidden files in your /home directory. It's possible that could mess with the permissions on those files and then screw up your Ubuntu installation. As long as you're handling personal files (movies, music, pictures, documents), it should be fine.

[Howto Thunderbird/Firefox profile share XP & Dapper](http://ubuntuforums.org/showthread.php?t=203524)

---

### Post by Uber-n00b on 2008-05-08
I've dual-booting Ubuntu (and Linux in general) with XP for about 2 weeks now. I split a 150GB HDD into 20GB NTFS (XP), 12GB Ext3 (Ubuntu), a 3GB Swap partition and the rest is formatted Ext3 I named *Data*. (<-- that's where my */home* dir is on Ubuntu.) The fs-driver's been pretty sweet! I've even managed to change the default locations of XP shells like *My Documents, Desktop*, and *Shared Folder* to their Ubuntu equivalents (*Documents, Desktop*, and *Public *respectively.) Interface has been pretty seamless except for 2 things really:
[LIST]
[*]Hidden Files & Folders
[*]Shortcuts
[/LIST]The Hidden Files & Folders thing I'd really like to resolve soon. (I don't need to see a *gnome-terminal.desktop* icon on my XP desktop for example.) If I try to make it hidden in XP, the changes don't seem to stick. Is this a XP/Ubuntu thing? Or is it the Ext3 file format? Will backing up, reformatting to FAT, and pasting everything back take care of this?

Also the shortcuts thing... Minor but def an annoyance. In Ubuntu when I try to open a shortcut created in XP, I get prompted to Run in Terminal, Display, Cancel or Run. Is there a way to bypass this dialog box and just Run everytime? 

Thanks all.

---

