---
title: "Failure to Recover from Ubuntu Crash"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Kurt_Alan on 2006-11-10
[FONT="Arial Black"][LIST][SIZE="4"][/SIZE]
[/LIST][/FONT]

****I'm starting my post again on the same topic because I'm not getting help.

I've suffered my second serious crash, where I will lose hundreds of hours of configuration time, if I cannot recover.  I can't continue to have this problem without a solution and still use Ubuntu.

Before the problem:  I used SBackup and saved only about 3 MB.  My media files were not backed up.  As a before and after check of df -h I found to my surprise that I had 0% space available.  I should have had 5 GB.  I then dumped a few hundred MB's of media files but df -h still showed 0% space available.  Obviously something is not right.  

The problem: When I re-boot, I fail to load GDM and return to the log-in screen.  I can enter tty1 but I don't know what to do there. Without my GUI, I'll just have to reformat, which I don't want to do.

Tried solution.  The forum advice was to boot from a Live CD, mount my hard disk and clear some files to boot normally and then identify the problem.

This is where I'm stuck: I read wiki on /etc/fstab and mounting.  I booted the Live CD, opened a terminal and typed ```
sudo mount /dev/hda1 /
```  I receive: ```
/dev/hda1 already mounted or / busy
```

I'd really appreciate some explicit advice on where I should go from here.](*,)

---

### Post by bodhi.zazen on 2006-11-10
I'm coming in the middle ....

Looks like the partition in question is already mounted.

Type:```
cat /etc/mtab
```to list all mounted partitions.

Then cd or browse into the partiton and check it out.....

---

### Post by podunk on 2006-11-11
Root is always busy. The Cd creates a hard drive in memory which it mounts as root.

The first thing is

cd /

to get to the root directory.

You need to create a mounting directory
```
sudo mkdir /media/lin
``` 
(you can use what ever you want, I recommend something very easy and fast to type)

Then
```
sudo fdisk -l
```
The above gives you a list of drives on your machine, make note of what you think is the root drive

```
gksu gedit /etc/fstab 
```
add this line 
```
/dev/hda1(or whatever)      /media/lin        ext3    defaults        0       2
```
note the spaces are really tabs.
save and close fstab
```
sudo mount -a
```
 the drive will be mounted. You can start nautilus in root mode:
```
gksu nautilus
```

If you have an extra CD drive you can move files off instead of deleting them

For your back up woes - Sbackup is good for keeping up with your data files, useless as a full back up.

Once you get back up install mondo from the package manager - it burns iso's to dvd's or cd's. You can restore the whole thing in about an hour.

---

### Post by Kurt_Alan on 2006-11-12
**[SIZE="5"][/SIZE]**

Thanks for all your help, everybody.  I'm printing your comments and much of this information will be useful.

By chance and playing I managed to solve my problem!  I found that I could start x in tty1 as root.  Then I got back my Home Folder, but it was under File System.

I searched and found an 8GB Sbackup file.  When I deleted this, my hard drive space returned and was confirmed by df -h.  GDM then loaded normally at log-on.

I think Sbackup was supposed to ignore 100 MB + folders by default.  But it didn't.  SBackup can be a dangerous tool for newbies!  Thanks again.

---

