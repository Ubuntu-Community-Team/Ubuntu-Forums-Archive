---
title: "[SOLVED] Ubuntu Partition Backup - Confusion"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-13
Hi there. I read through these forums and a host of other sites on the net concerning the best way to back up my Ubuntu partition(s). Unfortunately, being very new to Ubuntu I tend to get lost, and I don't fully understand what I'm reading, especially when instructions include complex essays that have to be typed into the command line.

**What I have:**
A hard disk set out like this:
Partition 1: Windows Boot partition
Partition 2: Windows Data
Partition 3: Windows Data
Partition 4: Secondary Windows OS
Partition 5: Ubuntu Boot Partition
Partition 6: Ubuntu Home
Partition 7: Ubuntu Swap

GRUB does the job of choosing Ubuntu or Windows, and the Windows boot does the job of choosing *which* Windows I want.

**What I want to do:**
Back up/Clone my main Ubuntu Boot partition, with something that will allow me to simply restore the whole thing back to where it was in the event that I trash it (Thats already happened a few times!). The backup will probably be far too large for a DVD, so I need the program to be able to burn the image onto multiple DVD's, or to allow me the option of saving it to 1) An external Hard disk, or 2) A separate internal NTFS drive (That is already found by Ubuntu anyway).

When I was using Windows a lot more I used Acronis True Image to make an Image of my partitions as required, but Iv read conflicting reports about how effective that actually is with Linux. So far I have looked at and failed to understand the following programs:

CloneZilla - Looks like it might be what I need, but I have no idea how to make it work.
G4U - Appears to want to back up to an FTP server.
Mondo - I cant work out if this is what I want or not even after a browse through the docs
mkCDrec - Similar to Mondo. I think.

Thats where Im at right now. Iv gone in circles a few times and no matter how much I read about it, nothing seems to make too much sense. 

My current thinking is this (PLEASE tell me if this is wrong!!)
If I boot into Windows (Remembering that GRUB is on the mbr of the first boot partition, which is Windows) I can use Acronis True Image to make an image file of my Ubuntu main partition, which, in the event of a catastrophe, can be restored to put me back where I was.

Any incompatibilities with Acronis and GRUB will be negated, since Ill be in Windows and GRUB is not on the partition that I want to back up.

If anyone has any other ideas, please tell me, and use really, *really*, simple language, preferably without delving into the command line much past 'sudo'!!

Thanks

Max

---

### Post by Moop on 2008-01-13
You don't need to type everything into the command line. Copy and paste works well. Also the CLI has a history so that you only need to type a specific command once. You can scroll through your previous commands with the arrow keys. 

If you want to back up your complete Ubuntu install you will need to back up your / and /home partitions. I've never used True Image with linux so I don't know how that works. I wouldn't worry about grub as it's easy to reinstall if needed. Burn a SuperGrub cd and you'll be prepared for any grub problems. 

Check out Psychocats link on doing backups. [http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by fiddledd on 2008-01-13
i have used True Image to back up my Ubuntu/XP Dual Boot for more than a year without any problems. Sometimes I image the entire Drive and sometimes I image 1 or more partitions. i have restored the root partition a number of times without errors. So I would stick with True Image. One thing to note is Linux can be backed while it's mounted (unlike Windows) so you can use tar to backup all files on the root partition.

EDIT:

Actually this link will explain about backup in more detail:

[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by MaxVK on 2008-01-13
Thanks for the replies.

Moop - I know I can copy and paste, but Iv been having some problems with that because sometimes the options switches '-' seem to get swapped with another character that appears just a tiny bit longer. I don't know why this happens, but in any case I'm trying to avoid copy and paste in favor of actually learning what it is that I'm typing!

I'm looking into the SuperGrub disk now - Seems like a sensible thing to have, thanks for the link.

fiddledd - I'm glad to hear that True Image works okay. Since I have the dual boot it seems wise to stick with what I know, for now at least. I can always learn about making backups when I have one that works! ;) 

Also, I followed your link and found another page ([here]("http://ubuntuforums.org/showthread.php?t=80790")) which has an automated backup script on it. Lots of people have posted that it works, but being (overly) paranoid about going through the whole Ubuntu installation again I wonder if you could tell me if this is a relevant script to use on Ubuntu 7.10?

Thanks again. Lets hope that I can get a decent back up done so I can at least rest easy the next time I start to mess about with something!

Max

---

### Post by fiddledd on 2008-01-13
> **MaxVK said:**
> Thanks for the replies.

Moop - I know I can copy and paste, but Iv been having some problems with that because sometimes the options switches '-' seem to get swapped with another character that appears just a tiny bit longer. I don't know why this happens, but in any case I'm trying to avoid copy and paste in favor of actually learning what it is that I'm typing!

I'm looking into the SuperGrub disk now - Seems like a sensible thing to have, thanks for the link.

fiddledd - I'm glad to hear that True Image works okay. Since I have the dual boot it seems wise to stick with what I know, for now at least. I can always learn about making backups when I have one that works! ;) 

Also, I followed your link and found another page ([here]("http://ubuntuforums.org/showthread.php?t=80790")) which has an automated backup script on it. Lots of people have posted that it works, but being (overly) paranoid about going through the whole Ubuntu installation again I wonder if you could tell me if this is a relevant script to use on Ubuntu 7.10?

Thanks again. Lets hope that I can get a decent back up done so I can at least rest easy the next time I start to mess about with something!

Max

I would think the Ubuntu version waouldn't matter as it's the same filesystem. However, there is a gui for you can try which will make your life a bit easier, this link will explain it and give you a download link of the latest version:

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462)

I have used QuickStart a few times and it seems to do what it claims without any problems. Hope that helps :)

---

### Post by MaxVK on 2008-01-13
Iv not found that one before! Thanks for that link - Ill follow it up ASAP. In the meantime I dropped back into windows and backed up my Ubuntu partition and my home partition with True Image. It all verified okay, but it wont hurt to have several backups from several different sources, just in case.

---

