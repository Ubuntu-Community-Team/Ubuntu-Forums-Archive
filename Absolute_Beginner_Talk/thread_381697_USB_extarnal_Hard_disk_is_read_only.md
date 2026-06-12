---
title: "USB extarnal Hard disk is read only"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by flavio newbie on 2007-03-11
Hello, I installed Ubuntu 6.10 yesterday, and i have a problem with my external hard disk:

It is NTFS and the files were all moved in from windows via usb, now that i am in ubuntu all files are read only, what shall I do?[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

I remind you guys that i never used the terminal, so please if you want to help me, explain as if you were talkin to a stupid.

thanks a lot guys.

---

### Post by Delvien on 2007-03-11
I would suggest backing up all the data on your external HDD, and reformatting the drive with ```
sudo GParted
```

Or run this from System>Admin from the panel. 

Select the drive from the drop down menu and right click the partition and then just reformat to ext3, fat 32 or otherwise, NTFS is a filesystem that does not work well with linux.

REMEMBER BACK UP YOUR INFORMATION ON THE EXT HDD FIRST

---

### Post by flavio newbie on 2007-03-11
Thanks man, i try it now

---

### Post by flavio newbie on 2007-03-11
ok i go to system, administration and then?
and if i backup the files, can i leave the backup on the hard disk? cause on my laptop i have 5 gb free and my external disk has 40 out of 80..
and how do i backup with linux? sorry, but i really never used linux, but i like it and want to be able to stick to it..

---

### Post by flavio newbie on 2007-03-11
ok gparted is being downloaded now from synaptic, i didnt have it... but the rest i still don't know

---

