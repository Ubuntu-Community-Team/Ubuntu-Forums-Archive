---
title: "Reinstalling Ubuntu on a different hard drive without moving my Home folder"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Greg K Nicholson on 2007-02-14
[Generic "Hi everyone! I'm new to Ubuntu and it rocks but I'd like a bit of help please" header]

I have two hard drives. One ("Nate") contains Windows XP and about 12 GiB free space; the other ("Brenda") contains Ubuntu 6.10 and about 12 GiB of files in my Home folder.

I'd like to do a clean install of Ubuntu on Nate (alongside Windows) and uninstall Ubuntu from Brenda; but keep my Home folder on Brenda and continue storing all my files there (i.e. on a different hard drive from Ubuntu).

I know how to do the clean install, but how would I go about uninstalling Ubuntu from Brenda without losing all my files? And (how) can I tell Ubuntu to use a second hard drive as my Home folder?

---

### Post by rverrips on 2007-02-14
> **Greg K Nicholson said:**
> [Generic "Hi everyone! I'm new to Ubuntu and it rocks but I'd like a bit of help please" header]

Welcome, glad you joined us ...

> **Greg K Nicholson said:**
> I'd like to do a clean install of Ubuntu on Nate (alongside Windows) and uninstall Ubuntu from Brenda; but keep my Home folder on Brenda and continue storing all my files there (i.e. on a different hard drive from Ubuntu).

I know how to do the clean install, but how would I go about uninstalling Ubuntu from Brenda without losing all my files? And (how) can I tell Ubuntu to use a second hard drive as my Home folder?

Ok, just some assumptions I'm going to make - Nate is a 40GB drive and currently consists of one partition, of which about 12GB is free.  Brenda is a 20GB drive, consists of two partitions, a swap partition (I'm guessing 1GB) and a root (i.e. /) partition of about 19GB?

I'm guessing (i.e. hoping) that  if you type df in your currently installed Ubuntu terminal window you see something like this:

[FONT=Courier New]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             40000000  28000000  12000000  67% /windows
/dev/hdb1             19000000  14000000   5000000  26% /
[/FONT]
I'd recomment you startup with the Ubuntu Live CD and then run gParted, which is tool that can be used to resize and create partitions.

Before anything else, you have to decide if you want to "move" your swap partition to Nate, or leave it on Brenda?

Either way, you have to resize the Windows partition (probably an ntfs or fat32 partition type) on Nate, and create a new empty ext3 partition in the space made available (i.e. the 12GB) - Don't worry 'bout labling it just yet, but I'm guessing it'll be referred to by the system as /dev/hda2

If you want to move the swap, then make the new ext3 partition on Nate only 11GB and create another partition of 1GB of the type "swap" on hda, and delete the swap (I'm guessing /dev/hdb2), otherwise, just leave /dev/hdb2 as is.

**Warning:** Although I've had huge success changing the size of Windows partitions, I have also killed entire systems using the gParted resize process (mostly my own stupidity, like resizing the partition while windows was actually in suspend-to-disk state, etc.) so make sure you have a backup of what's important on the Windows partition before doing any of this ... just incase.

Then run the Ubuntu installer from the Live CD and when asked about partitioning, choose manual.  

Choose the new partition you created on Nate (which I'm guessing was /dev/hda2) and select to mount it as / (i.e. root)

Select the ext3 partition (/dev/hdb1) on Brenda and make sure to leave the state as the same, i.e. do not format, etc. and mount it as /home.

When you're creating the users in yoiur new Ubuntu install, make sure you create 'em the order you did in the old one - Reason for this is user is given a UID, and you want these to match in the two Ubuntu installs, i.e. UID 100 is your user who has all the files in /home on Brenda (Try keep the username the same as well) - This isn't too serious, but makes things easier.

If you boot into your new Ubuntu you'll now see that under home  you'll have your old ubuntu system, i.e. /home/home will be the 12GB you had before and running df should look something like this:

[FONT=Courier New]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             28000000  28000000         0  100% /windows
/dev/hda2             12000000   2000000  10000000  17% /
/dev/hdb1             19000000  14000000   5000000  26% /home
[/FONT]
You can decide now if you want to clean up Brenda to "remove" Ubuntu that was installed on her - "rm /home/etc -fr" will clean out the old /etc folder - Do that command for everything else in /home except /home/home.

Then, to move your "old" home to where Ubuntu is looking for it now, simply do:
```
mv /home/home /home
```

If the UID's were the same, you'd done, if not, you may need to run: 
```
chown youruser:youruser /home/youruser -r
```
to sort out the permissions.

Hope that helps, have fun!

---

### Post by mssever on 2007-02-14
> **Greg K Nicholson said:**
> [Generic "Hi everyone! I'm new to Ubuntu and it rocks but I'd like a bit of help please" header]

I have two hard drives. One ("Nate") contains Windows XP and about 12 GiB free space; the other ("Brenda") contains Ubuntu 6.10 and about 12 GiB of files in my Home folder.

I'd like to do a clean install of Ubuntu on Nate (alongside Windows) and uninstall Ubuntu from Brenda; but keep my Home folder on Brenda and continue storing all my files there (i.e. on a different hard drive from Ubuntu).

I know how to do the clean install, but how would I go about uninstalling Ubuntu from Brenda without losing all my files? And (how) can I tell Ubuntu to use a second hard drive as my Home folder?

The easiest way to uninstall Ubuntu from Brenda would be to boot up a live CD, then mount the partition and delete everything **except** for the home directory. Then, ```
cd where/you/mounted/partition
mv home/* .
rmdir home
```Now, when you install, make sure that you choose the manual partition option, then set up Brenda to be /home. That's it!

---

### Post by Greg K Nicholson on 2007-02-15
Thanks, both of you, for your quick and helpful replies.

I only managed to reduce the Windows partition by 6 GiB—when I tried to reduce it further GParted complained that an extended record would be required and that this was not implemented—but I've taken 2 GiB out of the main partition on Brenda and mounted /usr there (now that I know it's so (relatively) simple to do such things).

The reinstall is happening now (live CD installation rocks) and it looks like everything's going according to plan. Again, thanks for your help.

---

