---
title: "missing files"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by 2eeks on 2006-11-14
So I went to start my ubuntu desktop today and it gave me an error that /bin/sh could not be found....


how do I go about getting this folder back to working order?

---

### Post by professor_chaos on 2006-11-14
In edgy /bin/sh is a symlink to dash

so from the commandline check to see if dash exists.

```
dash
```

if no problems, type "exit" to get back to bash if you want...then

check to see if the symlink exists

```
ls -l /bin/sh
```

if it doesn't then

```
sudo ln -s /bin/sh /bin/dash
```

---

### Post by moshuptrail on 2006-11-14
Is the folder /bin missing, or just the file? (sh)

The contents of /bin in part:
-rwxr-xr-x 1 root root 664084 2006-04-21 18:51 bash
lrwxrwxrwx 1 root root      4 2006-07-15 07:32 rbash -> bash
lrwxrwxrwx 1 root root      4 2006-07-15 07:32 sh -> bash

sh is a symbolic link to bash (Dapper)

---

### Post by 2eeks on 2006-11-14
ok now here's the wierd thing, when I go into the harddrive using the ubuntu install disk, I can see that sh is there... I dont know how to figure out if the system link exists, or modify it...


should I use recovery mode to get a shell so I can execute some commands?

PS. I checked the system link status using the install disk gui(right clicked the sh file and it says its a system link to /bin/dash, which exists), and it exists, but I dont know about dash. OK I just found the dash file... so it exists...

---

### Post by moshuptrail on 2006-11-14
What about PATH?

is /bin in your PATH?

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by 2eeks on 2006-11-14
ok here is some more depth to the error that is stopping the system, (I cant even boot into recovery mode)

init:Unable to execute /bin/sh for rcS: No such file or dir.
rcS process terminated with status 1
init:Unable to execute /bin/sh for rc-default: No such file or dir.
init: rc-default process (1974) terminated with status 1

---

### Post by 2eeks on 2006-11-14
I have about 11gigs of music on the current installation, would installing a second copy of ubuntu and then moving all of the files from one install to the other be possible through partitioning?

or would it all get erased in the process...

---

### Post by professor_chaos on 2006-11-14
Did your install seem to be sucessful with the exception of these errors.
Have you ever booted/logged in sucessfully.

From the sounds of it, your init scripts a missing (the scripts that start all of your system programs, such as your graphical interface, networking, etc). 

If you just recently installed, I would probably reinstall. I say this because I wouldn't know how to easily fix this. Maybe some else knows.

---

### Post by professor_chaos on 2006-11-14
> **2eeks said:**
> I have about 11gigs of music on the current installation, would installing a second copy of ubuntu and then moving all of the files from one install to the other be possible through partitioning?

or would it all get erased in the process...

11Gb, geesh. I guess you have sucessfully accessed your account.
Yes, you can make an new partition, install ubuntu and then copy your files over. Or if you have a usbdisk or other (fat or journaled type), you could boot the live disk and copy the files to this other drive.

---

### Post by 2eeks on 2006-11-14
I have sucessfully booted and logged in before. I was doing somethings this weekend to try to get 'make' working, I was unsuccessful and now this **** doesnt work...

Can I repartition and reinstall without erasing my data? That would just make it easier...

OK, so my fresh install of ubuntu will be able to read the old partion and just copy the files over right? will it be like looking at two different harddrives?

sorry for the newb questions, I just want to make sure I dont lose my music...

---

### Post by professor_chaos on 2006-11-14
> **2eeks said:**
> I have sucessfully booted and logged in before. I was doing somethings this weekend to try to get 'make' working, I was unsuccessful and now this **** doesnt work...

Can I repartition and reinstall without erasing my data? That would just make it easier...

OK, so my fresh install of ubuntu will be able to read the old partion and just copy the files over right? will it be like looking at two different harddrives?

sorry for the newb questions, I just want to make sure I dont lose my music...

Yes, if you have the one HD, then boot the live CD and when you get to the partitioner you can resize the current partition and then add a new partition with approx 15GB (11 for music and some to the OS). Then install on the 15GB partition and if successful, you will be able to mount the first partition as a "drive" and copy the files over. 
But...Remember, partitioning is not a completely "safe" procedure, and success is not guaranteed. I have never had problems doing this though.

---

### Post by dwblas on 2006-11-14
Do not reinstall until you get your files copied to a cd/dvd or some other backup or unused partition.  Loosing them is foolish.  You should be able to boot from the install disk and sudo to copy the files.  I use Knoppix for recovery so I don't know much about the install disk.  What are you doing that is giving you the error?  It may as simple as you have /bin/sh instead of !#/bin/sh in a bash file.

---

### Post by 2eeks on 2006-11-14
I get the above mentioned error when I try to boot... rcS or something...
I cancelled the repartitioning process... I dont want to lose this stuff...

please help me figure out what these errors are all about... Im gonna need this computer to get some projects done...

---

### Post by 2eeks on 2006-11-14
how can I copy the files?

How can I mount the first partition of ubuntu to get the files to a backup media?


do you really think I'll lose data if I just repartition?

---

### Post by dwblas on 2006-11-15
I don't think you will lose data if you repartition, but a reinstall usually formats the install partition which will remove everything.  As i said, I use Knoppix for rescue.  I would suggest that you download and burn a knoppix iso when you get the system back.  I found this thread on the forum on how to mount and copy Windows files from the live cd.  You can use this as a guide to backup your files.
[http://ubuntuforums.org/showthread.php?t=270609](http://ubuntuforums.org/showthread.php?t=270609)

---

### Post by 2eeks on 2006-11-26
So bottom line, if I attempt a reinstall, my files will live through the process or be completely destroyed?

I really need to get this computer working again, its my roomate's and he needs it for school.

---

### Post by steve.horsley on 2006-11-26
Reinstalling is likely to re-format the partition you install to, so this is not a good idea.

Using a live CD to resize the existing partition and thus make room for a fresh install is the best bet. I think the Ubuntu live CD comes with gparted that can do this. However, there is always a slim possibility of a screw-up so making a backup of your data first if possible would be a good precaution. A live CD should be able to mount your hard disk and copy the music to DVDs for you. Or perhaps if you borrow a second hard disk to copy it to for a while?

---

### Post by 2eeks on 2006-12-04
could someone tell me exactly how to go about mounting the ol partition to backup the music?

everytime I try to use sudo to mount the drive the terminal asks me for a root password... which doesnt seem right...

---

