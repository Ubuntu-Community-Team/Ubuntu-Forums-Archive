---
title: "Add a new, blank, hard drive"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Alex6969 on 2006-11-28
ok i have ubuntu on one 6.5 gb HDD, XP on a 20GB, and two other drives one a 30, and the other's an 80. these are all seperate drives. I've been running out of room on my ubuntu drive, so i added a second 6.5 GB to my computer. my question is, how can i set this drive up so that just ubuntu can use it, i cant see it in the media devices. how can i set this up for ubuntu?

---

### Post by CatKiller on 2006-11-29
First of all, you'll need to partition the drive. You can either use the Ubuntu Desktop cd, or the [GParted Live cd]("http://gparted.sourceforge.net/livecd.php") or, use the command ```
sudo aptitude install gparted
``` to do in in your normal Ubuntu install. If you only want to use this drive for Ubuntu you should format it as an **ext3** filesystem.

Then you will have to [mount]("http://en.wikipedia.org/wiki/Mount_%28computing%29") this partition into your filesystem. You might find [these instructions]("http://www.psychocats.net/ubuntu/mountlinux") useful for this. You might also consider using this drive to [house your /home directory]("http://www.psychocats.net/ubuntu/separatehome").

Good luck!

EDIT: > Darn. CatKiller beat me by seconds. ... 
Wow, that never happens!

---

### Post by K.Mandla on 2006-11-29
If I understand you correctly, hook up the drive and try this command. ...

```
sudo fdisk -l
```
That should show you where the drive has been assigned. From there you can edit /etc/fstab to mount it on boot. 

There are better and more complete instructions in the wiki: [uwiki]InstallingANewHardDrive[/uwiki]

Edit: Darn. CatKiller beat me by seconds. ... ;)

---

### Post by Alex6969 on 2006-11-29
ok i followed the instructions on how to move my home folder to the new drive, when it was all said and done, i couldn't log into ubuntu, it gave me the error, "Home folder moved, use root?" i clicked ok then it tried to log in and i got an xserver crash which took me back to the login screen. i can only get to the failsafe terminal succesfuly. i tried to restore what i had done, but to no avail. is there anyway i can fix this problem?

thanks for the quick replies. I don't want to have to boot back into windows :(

---

### Post by CatKiller on 2006-11-29
I'm afraid I've not done this procedure myself, so I can't tell what you'd have done wrong to get this error. The first message you've posted suggests that your /etc/fstab does not point to where you've copied your /home folder to.

The device name will depend on how the partition is connected to your computer:
[LIST]
[*]IDE drives start with a **hd**, SATA and SCSI drives start with **sd**
[*]The first drive is **a**, the second **b**, and so on
[*]The Primary partitions are numbered 1-4. Logical drives in an Extended partition are numbered from 5.
[/LIST]

So if the partition you made was a primary partition, and the drive you made it on is the second IDE drive in your computer, then the line you should put in your /etc/fstab will be something like ```
/dev/hdb1 /home ext3 nodev,nosuid 0 2
```

Otherwise, I really couldn't say which step didn't work for you.

---

### Post by Alex6969 on 2006-11-29
worked great thanks guys

---

