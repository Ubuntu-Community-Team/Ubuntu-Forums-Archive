---
title: "Re-Partitoned 2nd Hard-Drive Can't Write to it now"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-08-08
I re-partitoned my 2nd hard-drive, now I can't write to it. Under ddrive(the name of the 2nd hard-drive) properties, the owner is 'root' and it says I don't have permission to change any of the settings. I did make a directory named temp by using 'sudo mkdir /media/temp'. The folder is there, but as I said, I can't save anything to it because of the permission issue. 
As info, the first partition is ext3 file system and the 2nd partition is fat32 file system.
What can I do to get permission to write to the 2nd hard-drive?
Thanks in advance.

---

### Post by Stephen Howard on 2007-08-08
can you provide a copy of your /etc/fstab file?  Also, a copy of /etc/mtab might be useful.

---

### Post by Hopeless on 2007-08-08
sudo chown -R USERNAME:USERNAME /media/mynewdrive

also install ntfs config tool from add/remove progs to write

---

### Post by deaster2 on 2007-08-08
> **Hopeless said:**
> sudo chown -R USERNAME:USERNAME /media/mynewdrive

also install ntfs config tool from add/remove progs to write
This command did the trick...
MANY Thanks for the help

---

### Post by Hopeless on 2007-08-08
please keep in mind it's for the user only...so if you have a few users...you should check out the docs in [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

just a thought i 10 to 1 says you need to set up yer firewall properly....i downloaded firestarter and thought all was ok....Noooooo....check out [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

alot of good stuff in the community docs...

---

### Post by stinger30au on 2007-09-01
> **Hopeless said:**
> sudo chown -R USERNAME:USERNAME /media/mynewdrive

also install ntfs config tool from add/remove progs to write

thanks so much for this info, i managed to install a fhesh spare hdd, patritioned and formatted it mounted it, but could not write anything to it.
this has saved me ripping my hair out. 

Thanks again

---

