---
title: "[SOLVED] Backup Problems"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-08-25
So i have been trying to backup all day. I have tried Home user backup as well as simple backup and neither have worked. When i hit the backup now button for simple backup nothing happens. I tried doing a manual backup file by file but it is taking forever. When i use home user backup i get 2 error messages.

1.) It's recommended that you verify the integrity of the newly created backup archive.Would you like to proceed with verification? (Make sure the first medium of the newly created backup archive is accessible or loaded in drive)

2.) The media does not seem to contain valid HUBackup data.
Please make sure media #1 of your backup set is in drive and retry.(You can always use the "Verify" button independently)

Could someone walk me through this. I want to do a fresh install of feisty but i need to backup all my files to an external drive. i would prefer not doing it file by file.

Thanks in advance.

---

### Post by GMachine_24 on 2007-08-25
> **thesonisshining said:**
> So i have been trying to backup all day. I have tried Home user backup as well as simple backup and neither have worked. When i hit the backup now button for simple backup nothing happens. I tried doing a manual backup file by file but it is taking forever. When i use home user backup i get 2 error messages.

1.) It's recommended that you verify the integrity of the newly created backup archive.Would you like to proceed with verification? (Make sure the first medium of the newly created backup archive is accessible or loaded in drive)

2.) The media does not seem to contain valid HUBackup data.
Please make sure media #1 of your backup set is in drive and retry.(You can always use the "Verify" button independently)

Could someone walk me through this. I want to do a fresh install of feisty but i need to backup all my files to an external drive. i would prefer not doing it file by file. 

Thanks in advance.



I have no idea about home user this or that. As far as my experience, the only sensible (and simple) back up option for Linux is using the 'rsync' utility.

This link will take you to a thread I started as I searched for a way to back up an entire hard drive and the last post contains the information how I ended up doing it.

[http://ubuntuforums.org/showthread.php?t=140289&highlight=rsync+gmachine_24](http://ubuntuforums.org/showthread.php?t=140289&highlight=rsync+gmachine_24)


It's so easy it's almost embarassing.

gm

---

### Post by thesonisshining on 2007-08-25
Thanks for the response i appreciate it.

---

### Post by thesonisshining on 2007-08-25
I tried the way that was listed [here]("http://ubuntuforums.org/showthread.php?t=140289&highlight=rsync+gmachine_24")but i got an error

```
rsync: -avz/home: unknown option
rsync error: syntax or usage error (code 1) at main.c(1318) [client=2.6.9]

```

i want to back up my home folder to an external drive called IOMEGA_HDD. could you walk me through this?

---

### Post by GMachine_24 on 2007-08-25
> **thesonisshining said:**
> I tried the way that was listed [here]("http://ubuntuforums.org/showthread.php?t=140289&highlight=rsync+gmachine_24")but i got an error

```
rsync: -avz/home: unknown option
rsync error: syntax or usage error (code 1) at main.c(1318) [client=2.6.9]

```

i want to back up my home folder to an external drive called IOMEGA_HDD. could you walk me through this?

Hi. I can try to help. It would be a good idea to read through

[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

as an organized explanation can do a lot more than me throwing possible commands at you.

But, as a start, you need to put the location where you want to back up your files to in the same line as the rsync command.

Hence:

<code>


sudo rsync -avz /music1 ---force ---ignore-errors /musicbackup

</code>

This is the command I use to copy all files from the /music1 folder on my computer to the /musicbackup folder/directory on a separate hard drive. [Note: the -- before "force" and "ignore" are actually two hyphens, not three so - - force and - - ignore]

My /music1 folder is mounted on one hard drive, hde I think. The /musicbackup folder is mounted on the hdf drive. (If you need help with how to configure and mount hard drives/files, that is another matter).

The "force" and "ignore-errors" arguments are there because, without them, the back up will halt every time there is an error - and for some reason there seem to be a fair amount even though the resulting back up is a true copy of the original folder's contents. In other words, it seems to be ok to ignore the errors.

So, where is your Iomega drive folder/icon (i.e. IOMEGA_HDD) located on your Ubuntu machine? I assume it's in /dev or /media somewhere. (???)

So the command you would need would look something like this:

<code>

username@computername:/$sudo rsync -avz /home ---force ---ignore-errors /dev/IOMEGA_HDD

</code>

assuming your Iomega drive is mounted in the /dev folder with the name IOMEGA_HDD

If not, you need to substitute the path to the location of your Iomega drive.

Future back ups will use the exact same commands, but rsync will figure out which files are new and copy only those. There is also a command in the rsync program if you have copied a file previously from (in your case) /home to your Iomega drive but have subsequently deleted it from /home - this command (which I think is some form of 'delete') will remove all files on your Iomega drive that you have removed from your /home file - in other words rsync is really synchronizing your /home folder with the Iomega file - if you want it to. You can allow all files to remain on the Iomega drive if you want to, even if you have deleted them from your /home folder.

See, not so difficult.....

--gm

P.S. - OMG I just read the stuff at [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)    . Forget what I said; don't read it. It's unintelligible.

---

### Post by thesonisshining on 2007-08-26
WOW! That was awesome. That was exactly what i wanted. Thanks for all your help.It took a little time but i figured it out. Int the end it turned out to be sudo rsync -avz /home --force --ignore-errors /media/IOMEGA_HDD. It took about 35 minutes but it transferred all 11 GB. exactly.

---

### Post by GMachine_24 on 2007-08-27
Glad it worked out. :)

Now all future back ups are easy (meaning much faster) incremental back ups using the same command.

Hope you continue to enjoy Linux.

--gm

---

