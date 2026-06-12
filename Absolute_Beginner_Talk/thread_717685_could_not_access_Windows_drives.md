---
title: "could not access Windows drives"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-07
my friend installed kubuntu and whenever he tries to access Windows drives he gets the following error> hal storage fixed mount refused UID 1000.i am not sure whether he uses FAT32 or NTFS?

---

### Post by taurus on 2008-03-07
Perhaps your friend needs to mount his/her windows partition first before he/she can access it.  Open a terminal and post the output of this command here.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L, not number 1.

---

### Post by adi_das on 2008-03-07
he has tried mounting it and gets the same error

---

### Post by {BzF}~JOKesTER on 2008-03-07
Ask Your Freind If The Other Drive Shows In The "Computer" Folder In Ubuntu?

If So Ask Him To Double-Click It And See If It Opens 

Or Give You The Error Message And Post It On Here.:):)

---

### Post by Oldsoldier2003 on 2008-03-07
> **adi_das said:**
> he has tried mounting it and gets the same error

the reason we're asking for the fdisk -l output is the mount options are most likely stuffed. this will aloows us to see the device and partiton names next we'll likely want to see the contents of the file /etc/fstab

---

### Post by -random on 2008-03-07
press alt + f2 (to open the run box)
type 'konsole' and press enter, this'll launch you terminal.
then type:
sudo fdisk -l
then copy and paste the output into this thread so we can help you from there..

If it's a ntfs partition, just boot into windows and reboot into linux, it might be that the windows wasn't properly shut down..

---

### Post by taurus on 2008-03-07
I bet you he didn't shutdown windows cleanly the last time he used it.  Therefore, it will not mount even if you continue clicking it until the cows come home.  So, he can either boot back into windows and shut it down cleanly this time or use the force option to mount it in Ubuntu.

---

