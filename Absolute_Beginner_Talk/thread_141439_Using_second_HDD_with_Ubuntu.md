---
title: "Using second HDD with Ubuntu"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-08
I have 3 SCSI drives in my system.  2 are 16 GB and one is 70 GB.

Drive 0 runs Win Server 2003  (16GB)
Drive 1 runs Ubuntu Linux 5.10  (16GB)
Drive 2 has 2 partitions.  A 30 GB partition that is NTFS formatted to work with Windows and a 40 GB partition that I just formatted through Ubuntu Disk Manager I will call this the "Storage" drive.
The partition formatted fine and I marked it enabled.  The Disk Manager Utility can see the "Storage" Drive and even let me create a test folder on that drive.
When I go to Places > Computer, it does not see the Storage Drive, only the File System.
I tried creating a document through OpenOffice and saving it to the "Storage Drive", but I only have access to what I will call the File System Drive because I don't know what terminology to use.

Any suggestions on how I get Ubuntu to let me save files to this second drive?  Rebooting the system did not help.

Thanks

Wood

---

### Post by glug101 on 2006-03-08
Hmmmm.... I wonder if the drive is mounted properly.

Try opening a terminal and typing in the following:
```
df -h
```

And post the output here.

---

### Post by WoodyMahan on 2006-03-08
woody@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              16G  2.1G   14G  14% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile


This would seem to indicate that it is not mounted I guess.

---

### Post by glug101 on 2006-03-08
Actually, this might be a good sign :)  At the top of your gnome desktop there might be some buttons for mounting the drive.  Right click on this drive (likely named sdc1 or sdc2) and choose 'mount'.  

I don't remember all of the commands for doing this if the buttons aren't there.  It's been too long since I had a working Ubuntu box (all my x86 boxes are currently down :( ) but somebody here should be able to help you with the settings. :)

Best of luck! :D

---

### Post by WoodyMahan on 2006-03-08
Thanks for the help.  I will dig around a little more and hope someone else stumbles across the thread here as well.

---

### Post by glug101 on 2006-03-08
[QUOTE=WoodyMahan]Thanks for the help.  I will dig around a little more and hope someone else stumbles across the thread here as well.[/QUOTE]
Here's another idea.  SCSI is fantastic stuff, but a bit non-standard.  I would recommend possibly posting again, but this time just saying something like 'hard drive mounting help'.  The fact that the drives are SCSI doesn't affect this problem beyond Linux creating different names for the drives, and some Ubuntu users might say 'I don't know anything about SCSI' when they see your post.  You'll also get better coverage on the forums.  

Food for thought;)

---

### Post by WoodyMahan on 2006-03-08
Will try that. Thanks

---

### Post by psusi on 2006-03-08
You need to add a line to your /etc/fstab file describing where and how to mount the drive.  Create a suitable directory in /media, ex:

sudo mkdir /media/storage

Then add a line like this to /etc/fstab:

/dev/sda4 /media/storage ext3 defaults 0 0

Of course, you need to use the correct name for the partition instead of /dev/sda4.  

After that do a sudo mount -a and it should show up.

---

### Post by WoodyMahan on 2006-03-08
OK.  It showed up.  I can open and look at the volume, but when I right click, I cannot create new files or folders.  The option there is greyed out.  Did I miss setting some permissions?

---

### Post by glug101 on 2006-03-08
[QUOTE=psusi]You need to add a line to your /etc/fstab file describing where and how to mount the drive.  Create a suitable directory in /media, ex:

sudo mkdir /media/storage

Then add a line like this to /etc/fstab:

/dev/sda4 /media/storage ext3 defaults 0 0

Of course, you need to use the correct name for the partition instead of /dev/sda4.  

After that do a sudo mount -a and it should show up.[/QUOTE]
Hmmm, I knew about the command line method, but I thought there was some graphical way to do it in breezy.

---

### Post by psusi on 2006-03-09
[QUOTE=WoodyMahan]OK.  It showed up.  I can open and look at the volume, but when I right click, I cannot create new files or folders.  The option there is greyed out.  Did I miss setting some permissions?[/QUOTE]

sudo chown -R $USER.$USER /media/storage

That will change /media/storage and all files under it to be owned by you.

---

### Post by WoodyMahan on 2006-03-09
Awesome.  Perfect.  I am now setup the way I had envisioned from the start.

Thanks

---

