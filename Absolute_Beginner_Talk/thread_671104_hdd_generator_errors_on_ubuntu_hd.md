---
title: "hdd generator errors on ubuntu hd"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-18
i know this is a shot in the dark, but i was wondering- would anyone know of a reason why the utility HDD Regenerator (v1.5) would detect a great deal of bad sectors on a hard drive that Ubuntu 7.10 is installed on?  i know this might seem like a silly question, but i ask because i originally began having issues with this hd when it was used as my apps drive under Windows XP.. at that time i had run hdd regenerator on the disk several times and found at the very most just over 30 bad sectors on the disk (this was after at least 4 complete scans of the disk)- i have since performed a low-level format on the disk with the Maxtor Powermax utiltiy (it is a Maxtor 40GB drive) and ran perfermance tests on the disk to ensure it was in good working order, and installed the Ubuntu 7.10 system on the disk.  i tried scanning this disk with hdd regenerator again last night after ubuntu has been installed on the disk for about a week now, and it had found over 4,000 bad sectors! (all recovered) and this was only 3/4 of the scan progress- i had to abort the scan because it ran all night and was still not finished when i got up this morning!  i'm not sure why this would happen, and i was hoping someone might have a clue as to why hdd regenerator picked up so many errors this time around then it did why i first scanned the drive.  thanks.

---

### Post by SOULRiDER on 2008-01-18
Im probably wrong, but maybe it is designed to work on NTFS/FAT filesystems? If I were you i wouldnt worry about corruption, Ubuntu will take care of it and fsck will give you any errors if your data is corrupted.

---

### Post by Matt26 on 2008-01-18
it says it will work on NTFS, FAT and any other filesystem (which i am assume means any Linux filesystems)... but it says that it does not look at the filesystem when scanning for bad sectors and data remains unaffected.  what is fsck?  how does Ubuntu take care of any corrupted data?

---

### Post by SOULRiDER on 2008-01-18
After mounting your drives a certain ammount of times (30 actually) fsck will be run and will check your partitions for errors. You can run it manually too.
Boot the live CD and in a terminal run
```
fsck /dev/sda1
``` or whatever your linux partition is.

**DO NOT USE ON A MOUNTED FILESYSTEM**

If theres an error in the filesystem is found fsck will attempt to fix it.

Also, check this out:
[http://ohioloco.ubuntuforums.org/showthread.php?t=77771](http://ohioloco.ubuntuforums.org/showthread.php?t=77771)

---

### Post by Matt26 on 2008-01-18
thanks for all the information.. i will try this when i am back at my computer- as a possibility, if i run this command and it finds nothing wrong with the disk, what might this indicate?  regardless of the outcome, the resuts of the hdd regenerator scan still show a great deal of bad sectors that were recovered- is there any significance to this?  i would hate to ignore this if it means that there may be an issue with the disk.  does the fsck command only check the linux partition, or does it check the entire disk linux is on?  hdd regenerator scans the disk itself and does not check the filesystem (as is my understanding) so is it possible that the fsck command will not pick up any issues on the disk if they are indeed present- as indicated by hdd regenerator?  thanks.

---

### Post by SOULRiDER on 2008-01-18
fsck hill check the partition you want. I highly doubt that if there is somehting wrong with the disk fsck will not pick it up. If fsck shows no problems at all im guessing HDD regenerator was wrong.

---

### Post by Matt26 on 2008-01-20
i tried fsck after booting my computer from the live CD- i was able to scan the /dev/sda1 partition and it came up clean.. however when i tried to scan both the sda2 and sda5 partitions i received an error message stating something about a superblock and that this partition could not be found and that if does exist it may be corrupted.  sorry for the lack of details on the error mesage- if necessary i can try a screenshot of the message i'm receiving (anyone know i do a screenshot in Linux?)  so i'm not sure if i did the scan right or if maybe i really do have an issue here... any ideas/suggestions are greatly appreciated.

---

### Post by torgrot on 2008-01-20
What filesystem is on sda2 and sda5?  fsck only works on ext3 filesystems, not fat, ntfs or swap partitions.

---

### Post by Paulmd on 2008-01-21
> **Matt26 said:**
> i tried fsck after booting my computer from the live CD- i was able to scan the /dev/sda1 partition and it came up clean.. however when i tried to scan both the sda2 and sda5 partitions i received an error message stating something about a superblock and that this partition could not be found and that if does exist it may be corrupted.  sorry for the lack of details on the error mesage- if necessary i can try a screenshot of the message i'm receiving (anyone know i do a screenshot in Linux?)  so i'm not sure if i did the scan right or if maybe i really do have an issue here... any ideas/suggestions are greatly appreciated.


I have a great deal of mistrust for utilities that claim to physically repair bad sectors. Diagnose your hard drive with the proper tools.  Download the diagnostic utility from the manufacturer of your hard drive. Seatools from Seagate will do if you don't know/can't find the correct info. Seatools works with non-Seagate drives.

If seatools says you have EVEN ONE bad sector, do not try to repair the drive with HDD Regenerator. Instead, recover your important data, then replace the drive.

---

### Post by torgrot on 2008-01-21
> **Paulmd said:**
> I have a great deal of mistrust for utilities that claim to physically repair bad sectors. Diagnose your hard drive with the proper tools.  Download the diagnostic utility from the manufacturer of your hard drive. Seatools from Seagate will do if you don't know/can't find the correct info. Seatools works with non-Seagate drives.

If seatools says you have EVEN ONE bad sector, do not try to repair the drive with HDD Regenerator. Instead, recover your important data, then replace the drive.

I whole heartedly agree with Paulmd.  I went to the site for hdd generator and took a look.  When a hard drive starts reporting bad sectors the drive is not long for this world.  Magnetic reversal sounds like fish oil to me.

torgrot

---

### Post by Matt26 on 2008-01-21
thanks for the details torgrot- the sda2 and sda5 partitions are extended and swap partitions (in that order i believe) so maybe that's why it didn't work on those?

i have read a number of reviews on the HDD regenerator software and everything that i have read indicates that it is a very reliable and effective utility... i would like to believe that is the case, as i have used this utility many times in the past to restore other hard drives and it has worked for me in the past, but not always.

---

### Post by Paulmd on 2008-01-21
> **Matt26 said:**
> thanks for the details torgrot- the sda2 and sda5 partitions are extended and swap partitions (in that order i believe) so maybe that's why it didn't work on those?

i have read a number of reviews on the HDD regenerator software and everything that i have read indicates that it is a very reliable and effective utility... i would like to believe that is the case, as i have used this utility many times in the past to restore other hard drives and it has worked for me in the past, but not always.

AND? Does a proper diagnostic tool indicate that your drive has bad sectors or not?

Seriously, once a drive develops even one bad sector, odds are very high that it will be entirely useless in short order.


"After the first scan error, drives are 39 times
more likely to fail within 60 days than drives without
scan errors. "

[http://research.google.com/archive/disk_failures.pdf](http://research.google.com/archive/disk_failures.pdf)


Don't mess around. If your hard drive has bad sectors, recover data and replace.

---

### Post by Matt26 on 2008-01-21
i have used the diagnostic utility for the drive (PowerMax for Maxtor HD) and it did report 1 error on the hard drive the first time it was running a low-level format on the drive i believe- i don't recall the error being specific about what the issue it encountered, but if i remember correctly, there was a counter keeping track of the sectors being formatted and this is where it encountered the error.. interestingly i ran the format a couple more times afterwards and it did not encounter this error again.. not sure if this error meant anything or not, but i haven't encountered any obvious or noticeable issues with the hard drive since, just the report from HDD regenerator stating that there were a number of bad sectors (which it also said were repaired).

---

### Post by Paulmd on 2008-01-21
> **Matt26 said:**
> i have used the diagnostic utility for the drive (PowerMax for Maxtor HD) and it did report 1 error on the hard drive the first time it was running a low-level format on the drive i believe- i don't recall the error being specific about what the issue it encountered, but if i remember correctly, there was a counter keeping track of the sectors being formatted and this is where it encountered the error.. interestingly i ran the format a couple more times afterwards and it did not encounter this error again.. not sure if this error meant anything or not, but i haven't encountered any obvious or noticeable issues with the hard drive since, just the report from HDD regenerator stating that there were a number of bad sectors (which it also said were repaired).

I take it that you ran PowerMax a long time ago, has it been run AFTER the hdd regenerator report? 

If it's clean, you're fine, if not, then i stand by the advice to recover data and replace. 

Once upon a time, hard drives SHIPPED with a list of bad sectors printed on them, that were present from imperfections in the manufacturing process. A low-level format is supposed to map these out, and give you the appearance of an error-free drive. 

Modern hard drives come from the factory already low-level formated, And the firmware automatically reallocates bad sectors that develop from spares. 

Some utilities take advantage of this, to hide bad sectors. This is most likely what hdd regenerator really does. It stops working when the spares have been allocated.

---

### Post by Matt26 on 2008-01-22
well i tried running powermax again last night on the drive and sure enough, after the advanced scan had been running for about 20 minutes or so, it reported an error code, drive failure detected etc.

thanks to all for the help on this post, i plan on making an image of the drive tonight and replacing the drive.  anyone have suggestions on the best utility for a hard drive backup and restoration procedure?

---

### Post by Paulmd on 2008-01-22
> **Matt26 said:**
> well i tried running powermax again last night on the drive and sure enough, after the advanced scan had been running for about 20 minutes or so, it reported an error code, drive failure detected etc.

thanks to all for the help on this post, i plan on making an image of the drive tonight and replacing the drive.  anyone have suggestions on the best utility for a hard drive backup and restoration procedure?

With bad sectors, cloning is dicey. If you want the replacement copy to be a working OS. I've created clones of bad drives in attempt to recover data. The issue with getting a working OS out of clone of a bad drive is that important system files may be damaged.

On Linux there is a utility called ddrescue (you have to compile it). It works pretty well.

[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

You may instead want to copy your personal data, and make a list of applications you need to restore. Then generate a text file you can run, to install them.

For example ```
sudo apt-get install thunderbird xmss and_whatever_else
```

You may get away with the clone, and only have to reinstall one or two damaged apps. But you never know for sure. Pay attention to the error count, if it's say less than 10, then chances are good there's little risk in getting the clone to be a workable os. The bigger the count, the greater the odds that something really important is damaged, and the clone is only good for salvaging your data.

---

### Post by Matt26 on 2008-01-24
are there instructions available for how to install and use ddrescue?  thanks.

---

### Post by Paulmd on 2008-01-24
> **Matt26 said:**
> are there instructions available for how to install and use ddrescue?  thanks.

1) download, and extract the latest version

[http://ftp.gnu.org/gnu/ddrescue/ddrescue-1.7.tar.bz2](http://ftp.gnu.org/gnu/ddrescue/ddrescue-1.7.tar.bz2)

2) If you have never compiled anything on your computer, you need to install build-essential
```
sudo apt-get install build-essential
```

3) navigate to the directory where you extracted ddrescue

4) Build the project
```
./configure
make
sudo make install
```

5) ddrescue [input] [output]

for example 

```
sudo ddrescue /dev/sda1 /dev/sda2
```

Verify the correct devices first!!!!!! Do this wrong and you can overwrite the source! This is an example for illustration only, your devices may be different!


Ideally, this should be run on a system where neither the source drive, nor the destination drive are currently running an os. You may want to scrounge up a small hdd (down to around 10gb), install a barebones ubuntu on it, and attach your 2 other drives as secondary devices.

Oh, yes, Verify the correct devices.

ddrescue can also be used to rescue individual files, as well as output to an image file.

---

### Post by Matt26 on 2008-01-24
thanks for the information- is there a way that i can verify that i have build-essential on my system?  i think i may have it but i'm not sure..

also, would it be safe to run this command from the livecd?

---

### Post by Paulmd on 2008-01-24
> **Matt26 said:**
> thanks for the information- is there a way that i can verify that i have build-essential on my system?  i think i may have it but i'm not sure..

also, would it be safe to run this command from the livecd?

Well, if you run the apt-get command, and build-essential already exists, you will get a message saying so. :)

You can also check in the synaptic package manager.

I think it would be safe to run from the livecd,

---

### Post by Matt26 on 2008-01-24
also, is it possible to use this command to specify an entire hard disk to be backed up, rather than just the partitions?  if not, is there an alternative solution that would allow me to do this?

thanks again for all your help :)

---

### Post by Paulmd on 2008-01-24
> **Matt26 said:**
> also, is it possible to use this command to specify an entire hard disk to be backed up, rather than just the partitions?  if not, is there an alternative solution that would allow me to do this?

thanks again for all your help :)

yes.

once you get it built, type ddrescue --help

I forgot the syntax, it should be 

ddrescue [options] input output logfile

And yes, ddrescue is not only disk imaging tool that will work. It just happens to be the one I've used. Also, it's tolerant of bad sectors, which many utilities do not do well.

---

### Post by Matt26 on 2008-01-24
ok- would you be able to suggest an alternative to ddrescue that works well?  thanks.

---

### Post by Paulmd on 2008-01-24
> **Matt26 said:**
> ok- would you be able to suggest an alternative to ddrescue that works well?  thanks.

Not that I have used myself. Googling turns up a few.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Bear in mind, Ideally cloning is done from error-free disks to error-free disks. I do not know what the results will be WHEN they encounter the bad sectors on your disk.

I know ddrescue deals with them fine. But most apps, once they see a bad sector, they give you an error message and abort the copy.

---

### Post by Matt26 on 2008-01-25
thanks- i did a disk-to-disk copy with Acronis True Image Server and, although the copy process was painfully slow (took about 18 hours copying from a USB drive), the copy process was completed successfully.  i then performed a number of disk checks with powermax, hdd regenerator, ubuntu fsck, and they all came up clean.  Ubuntu boots fine now (although it seems a bit slower to start after the login screen than i remember) so hopefully it is safe to say that my new drive is good to go.

one interesting note- when running any partitioning utilities from a bootcd (Hirens) with the failing HD attached via USB enclosure (or IDE for that matter), i would notice that the mouse pointer would 'jump' around the screen sporadically, in doing so it would also invoke different commands from whatever screen i was on while this was happening- like it was emulating mouse clicks on different buttons on the screen/resizing dialog windows when all i was doing was moving the mouse pointer around- very bizarre!  plus, every few seconds or so i would hear would i could only describe as a series of 'beep' codes- similar to what you would hear in a PC when it doesn't POST and fails due to a hardware issue.  my guess is that somehow the failing HD was causing this behavior- has anyone ever encountered or heard of anything like this before?

---

### Post by Paulmd on 2008-01-25
> **Matt26 said:**
> thanks- i did a disk-to-disk copy with Acronis True Image Server and, although the copy process was painfully slow (took about 18 hours copying from a USB drive), the copy process was completed successfully.  i then performed a number of disk checks with powermax, hdd regenerator, ubuntu fsck, and they all came up clean.  Ubuntu boots fine now (although it seems a bit slower to start after the login screen than i remember) so hopefully it is safe to say that my new drive is good to go.

one interesting note- when running any partitioning utilities from a bootcd (Hirens) with the failing HD attached via USB enclosure (or IDE for that matter), i would notice that the mouse pointer would 'jump' around the screen sporadically, in doing so it would also invoke different commands from whatever screen i was on while this was happening- like it was emulating mouse clicks on different buttons on the screen/resizing dialog windows when all i was doing was moving the mouse pointer around- very bizarre!  plus, every few seconds or so i would hear would i could only describe as a series of 'beep' codes- similar to what you would hear in a PC when it doesn't POST and fails due to a hardware issue.  my guess is that somehow the failing HD was causing this behavior- has anyone ever encountered or heard of anything like this before?

Well, any failing piece of hardware can cause random badness.

If I saw just that, described as a symptom, I admit bad hard drive wouldn't be my first guess.  I would say something like, "get a new mouse."

---

### Post by Matt26 on 2008-01-25
well i believe the failing hard drive may be the culprit here, as i had run these same utilities without the failing hard drive hooked up and the utilities ran fine... i just hope this didn't affect any other hardware on my system or my other hard drives.

---

