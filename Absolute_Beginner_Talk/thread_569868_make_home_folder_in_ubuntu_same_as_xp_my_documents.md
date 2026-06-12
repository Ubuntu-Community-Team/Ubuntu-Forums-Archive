---
title: "make home folder in ubuntu same as xp my documents"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by koidenouvo on 2007-10-07
Hi,

Now that Ubuntu can read and write ntfs, which solution is best to have the Ubuntu home folder be the same as Windows My Documents?

I have read different threads but as ubuntu 7.10 is available, (i haven't installed it) will it be then possible with this ntfs read and write tool to set a common ubuntu/windows xp my documents/home folder? That means when installing Ubuntu, in the partitioning menu, we can choose ntfs for home folder? (i know from reading previous threads, permissions and security settings currently work on ext hd (ubuntu 7.04 and prior) but can this be configured another way?

Or is that tool Ext2 Installable File System for Windows a better way to achieve this?

Please let me know of any solution and how to implement it if there is any command line, mounting or unmounting lines to deal with.

Pascal

---

### Post by hotweiss on 2007-10-07
See if Ubuntu Tweak doesn't let you do what you want:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by kwiter on 2007-10-07
I've a similar question, I have both Mac OSX 10.3.9 on this iMac along with Ubuntu 7.04 and DON'T want to have 2 Music libraries. Going crazy with chmod trying to open the users/me/music to use in Ubuntu. 

Nia:wen kowa Many Thanks from Mohawk National!

---

### Post by nick_h on 2007-10-07
You have a few options:

1. Mount your windows partition using ntfs-3g which has write support.  Then simply create a symbolic link under your home directory.  If you link it to the Documents directory then you can access it from the places menu.

```
ln -s /media/<mount point>/Documents\ and\ Settings/<windows user>/My\ Documents/ /home/<ubuntu user>/Documents/
```

2. Don't use the Windows My Documents or your Ubuntu home directory to store your data.  Create a separate partition for it.  If you choose NTFS then use ntfs-3g, if you choose ext2/3 then there are Windows drivers available, if you use FAT then no additional drivers are required but FAT does have its limitations.

3. Create a separate partition for your Ubuntu home directory.  In Windows you will also be able to see the Ubuntu confguration files which you may not want to.

---

### Post by koidenouvo on 2007-10-07
Thanks all for this,

(Ubuntu tweaks didn't help me for this matter, although the idea of Ubuntu tweaks is very nice and should be explored further).

nick_h, from your option, i'll choose the first (is it being modern huh?

However from choosing this option will i reach my goal? That is the link is my home folder will be the place where documents from every application will be saved by default (dowloads from browsing the web, any other application documents save as...).

Why am i looking for this? Because of having ubuntu home folder on one partition and windows xp home folder on another, I find myself with 2 copies of a document when cleaning my ubuntu desktop or windows desktop and one copy finaly ends up in the bin.

Maybe this last view will bring new option, but i liked the first one although i haven't implemented it yet, i will anytime soon,

Thanks again

---

