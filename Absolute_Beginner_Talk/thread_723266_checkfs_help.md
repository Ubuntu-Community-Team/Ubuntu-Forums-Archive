---
title: "checkfs help"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2008-03-13
So i get an error and it tells me its put a log in /var/log/fsck/chekfs
here are the contents of said file:
Log of fsck -C -R -A -a 
Thu Mar 13 10:07:56 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=1ae48e60-5971-48b9-ab09-017ed582bb40'

/dev/sda4: clean, 80219/2080768 files, 614030/8307613 blocks
fsck died with exit status 8

Thu Mar 13 10:07:56 2008
----------------

BTW, this always happens.
I get it. A superbllock is bad, possibly. How do I fix it, though?

---

### Post by plucky on 2008-03-13
miesnerd,

Have you been able to continue to boot after the failure?

You should be able to press enter and then Ctrl-D to allow the system to boot.

After you login,open a terminal and copy and paste ```
cat /etc/fstab
``` and ```
blkid
```
You will find that one of the **UUID's** in your **fstab** file doesn't match what you get from the **blkid** command.

To edit the fstab file, after you make a copy of it, is to ```
gksudo gedit /etc/fstab
``` and change the incorrect UUID to the correct one.


Good Luck

---

### Post by miesnerd on 2008-03-13
> **plucky said:**
> miesnerd,

Have you been able to continue to boot after the failure?

You should be able to press enter and then Ctrl-D to allow the system to boot.

After you login,open a terminal and copy and paste ```
cat /etc/fstab
``` and ```
blkid
```
You will find that one of the **UUID's** in your **fstab** file doesn't match what you get from the **blkid** command.

To edit the fstab file, after you make a copy of it, is to ```
gksudo gedit /etc/fstab
``` and change the incorrect UUID to the correct one.


Good Luck
i have indeed been using  ctrl -D and been able to use the system very well, with only a few instances of problems with firefox and wicd (but those happen to some extent anyways, beucase my wireless is not great; signal is very far away).

So did I totally misinterpret this and think that a block was bad on my drive?

---

### Post by plucky on 2008-03-13
> So did I totally misinterpret this and think that a block was bad on my drive?

Yes,This problem is caused by the UUID of a partition being different to what is in /etc/fstab file

Please open a terminal and copy and paste the outputs of ```
cat /etc/fstab
blkid
``` so that we can see which partition has changed.

Have you noticed that a partition hasn't mounted?

---

