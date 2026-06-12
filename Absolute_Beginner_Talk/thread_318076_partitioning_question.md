---
title: "partitioning question"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by dross on 2006-12-13
Hello,
I am trying to create a dual boot scheme on my Dell laptop. I had planned to take the largest parition on my computer that currently has Windows on it, and divide that up for Ubuntu and Windows.  Unfortunately, Dells don;t seem to ship with the operating system on CD anymore...all I have a separate partition that is used to restore shipping condition.  So, in short, if I try to divide up this partition and install Ubuntu on one of those pieces, I'll erase the Windows data and won;t have a way to reinstall Windows on just the remaining new partition (because it will just return the disk to its original condition)...any one run into a similar problem?

---

### Post by Spif on 2006-12-13
If Windows and the factory standards are not on the same partition, resizing the Windows partition won't destroy the other.

In fact, you can partition an NTFS drive without ruining any data whatsoever. I did that myself on my IBM X60s. Taking backup is always a good idea though, like 1% of the time it can go wrong.

---

### Post by TyphoonJoe on 2006-12-13
If you cannot re-install windows then you have to re-partition without affecting windows.

1) Run a defrag to move all windows data to the beginning of your existing windows partition.  

2) Use a tool like "Partition Magic" to split your windows partition somewhere after the point you actually have data.  *As always when partitioning be sure you have good backups.  Partition magic has never failed me, but I still take backups every time I use it.

3) Install Ubuntu on your new linux partition!

And yes, Dell sucks and they don't ship a vanilla Windows XP CD like they should. ](*,)  But they ALWAYS give you the OS on CD somewhere, it may be labeled "System Restore" or something...  Not a Dell user myself but most vendors ship Windows (in Disguise on some restore CD).

best of luck!

---

### Post by lyceum on 2006-12-13
One work of advice that cannot be said enough...

Back **everything** up **first**!!!!! 

Not trying to be rude, it is just sound advice. Also, if it did not come with a disk, some companies are putting the re-install on a hidden partition on the hard drive. If you don't have a disk, you can call their customer service line and get more info.

---

### Post by dross on 2006-12-13
Hi everyone,
Thanks for the help! Spif, I am not worried about overwriting the backup partition, its just that there is no way to control the restore/reinstall that the windows backup partition performs.  so it would return my machine to original condition...erasing the linux partition I had created.  So, I guess I'll just get partition magic and give that a go.  Thanks a lot!

  

And, speaking of backing  up files...I just used [MozBackup]("http://mozbackup.jasnapaka.com/") to backup and then restore my FF and Thunderbird settings/email/etc when I wiped/restored the Dell laptop we are talking about...it was pretty sweet; it preserved all my email and RSS feeds with little fuss...not sure how well known this tool is, but I highly recommend. Thanks again!

---

### Post by real_ate on 2006-12-13
just noticed your thread and i thought i'd give my 2cents :)

i just installed ubuntu on my big machiene yesterday and did all the nonsense with repartitioning... i didn't find it too difficult at all, i didn't even back up my data! (althogh i would advise backing up, i just didn't care about my stuff is all) 

the only 2 things that i did was:
   1. Defrag. and i did it with all my processes turned off, i would have done it in safe mode for a better result but my comp is doing strange things at boot time :/
   2. Defrag again! keep doing it and it sorts out your white space better :)
   3. Install ubuntu! i spent about half an hour working with my partition table but all i used was the tool the ubuntu have on their install cd. it really helped! i resized my windows partition, created swap, made my linux partition, made a fat32 disk for my stuff and then to top it off i made myself a home directory aswell! may be a little bit of over-kill but hey! i like it :)

---

### Post by dross on 2006-12-13
Thanks for the input.  Are you saying that you used the Ubuntu built-in partitioning tool (in the installer) and were able to resize your windows partition are it didn't erase that partition?  From reading [this page]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html"), I was under the impression that any change to an existing partition would wipe it.   And don;t all bootable partitions need to be in the first 1028 of the HD? 

Also, a sort of unrelated question, I already have 3 primary partitions on this laptop (on is the big windows partition, one is the restore partition that Dell put on there, and I have no idea what the other one is..), and I'm not sure how to create a / and a swap with just one primary partition...if I create the / as primary, I can't create any new partitions....if I create an extended partition, the / won't be a primary partition.

---

### Post by Spif on 2006-12-15
Yes, I resized a partition with Windows XP and NTFS on it without losing any data whatsoever. Very easy to do this. In some rare cases it can go wrong, though, so remember to backup!

---

### Post by dmartinsca on 2006-12-15
Instead of downloading a pirated version of or spending money on (haha, yeah right!) Partition Magic, I always use gParted. It comes as a live cd or live usb to boot your computer with and do the partitioning, it's only about a 30MB download, and best of all it's free. I agree that you should defrag your windows partition before starting, although I've resized NTFS and fat32 partitions before without defragging and things went fine.

---

### Post by az on 2006-12-15
> **dross said:**
> I'll erase the Windows data and won;t have a way to reinstall Windows on just the remaining new partition (because it will just return the disk to its original condition)?

Actually, the backup-restore option they tend to ship cannot gurarantee to protect your Ubuntu installation.

As well, I am not sure how well it plays with partitioning.  I don't know that if you change your number of partitions, or order of partitions, it can safely continue to work.



> **dross said:**
> 
...any one run into a similar problem?


Yes.

I phoned Dell and asked if their backup solution would work well with a hard drive that was partitioned and had linux installed.  They could not give me an answer.

I told them that their restore solution was therefore inadequate.  They agreed and within several seconds, they had aranged for a bunch of cds to be shipped to my house at no charge.

So, you should phone them and ask.

---

### Post by dross on 2006-12-16
Haha, done, just got my CD's yesterday...so I guess I'll proceed hoping that the Dell partitions won;t fail, but with that backup CD's so I'll be ok if they do.  Thanks!

---

