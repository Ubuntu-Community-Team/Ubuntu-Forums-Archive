---
title: "need help re: replacing bad hard drive and how to get all files to new HD"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-06-11
Hi:

I don't think my explanation is very clear so let me try this:

For the past week or so the main hard drive in my computer (running Edgy Eft) had been making 'clicking' noises .... then the screen would freeze.... error messages sometimes on a reboot. I decided the main problem was my hard drive - it had been in use for about five years - so I got my Edgy install disk out, installed a new hard drive and then installed the OS. I configured the computer so it can read/write to the other (count 'em, 3) hard drives used for back ups of yet other computers, some video and audio and, perhaps most importantly, email.

I had been backing up the main hard drive every couple of days so I have like... 10 backups, the most recent being May 30. I know that is awhile ago but the trouble with the hard drive made it difficult to do another, more recent, back up before installing the new hard drive.

I suppose I should say the computer runs great - amazingly faster than it was before. I guess an uncrowded hard drive that isn't disintegrating is responsible.

Anyway, I have some documents backed up in a folder on one of the other hard drives - so restoring them is no sweat. But I'm wondering about everything else - the only thing I can think of that really matters are my emails and calendar (appointments). I know these are backed up onto the tar files which hold the computer's back up information - and I think as long as I can restore those I am happy to reinstall software and whatever else I need to do so the computer is back in full operation.

The other choice is to unzip and install the information from the most recent tar file - it is about 850MB and includes everything - email, programs (open office, etc.) But I am concerned perhaps the data is corrupted (which could help explain the problems I had along with the dying hard drive) and so I'm not sure I want to do this -- you know, using this kind of command

user@computername:~$ tar xvz /tarbackups/ubuntubackup.tar.gz  /

Plus I think if it does become necessary I can always do the restore in a week or so if some problems develop. Meanwhile, I can find the files I want to transfer by searching through the archive file . . . at least this is what I think I can do. As I said, transferring my Evolution files is my main concern.

Even though I've used Linux on-and-off for about a decade I still have a lot to learn which is why I am seeking help for this - I figure I can't be the only one who has had to replace a dying hard drive.

Thanks in advance.

gm

---

### Post by longlegs on 2007-06-12
Hi,
I don't know a lot about linux yet but I'm an old hand with hard drives. I strongly recommend that you use the failing HDD for nothing except recovery, and that the probable safest method is to do the equivalent of using Nero (a windows app) to make an ISO image of the drive. This will place the least load on the head mechanism and will get ALL the info. Good luck.
Longlegs

---

### Post by GMachine_24 on 2007-06-12
Thanks for your reply.

Actually, there is a version of Nero for Linux - I have Nero on my Windows boxes as well as Roxio. But back ups on Linux are different/easier (IMO) than on Windows machines and you can pretty much just create a tar file with whatever information you want to copy from your hard drive.

Linux does not have some of the problems / issues with back ups that Windows does (there is a lot of information about this on the Net so I won't repeat it here).

Anyway, I have the old hard drive but don't plan on using it for anything. As I said, I have numerous back ups of the system and these are all on a different hard drive - i.e. not the one that is crumbling.

Hope you grow to enjoy Linux. I think it's great.

gm

---

### Post by timcredible on 2007-06-12
just replace the hd, re-install the system, and restore your files from the tar file (if you double-click on a .tar file, ark will automatically open up and show the files in the tar file so you can pick and choose the files/directories you want to restore).  i've done this many times when installing a new computer.  i typically just do a 'sudo tar -cvf /backup.tar /home' which picks up all user's files.  flash drives are nice as the storage media for the tar files.  i just bought a 4gb sandisk flash drive for $32 on ebay.  for larger files, i use a 100gb external usb-powered hard drive (about $80).

---

### Post by GMachine_24 on 2007-06-12
Thanks for your reply.  I went ahead and reinstalled the next-to-most-recent tar backup and so far everything is working fine. I did this partly because, as I started to recreate the computer configuration, I realized how much work it was going to be.......

It was kind of cool to see pics and icons popping up on the desktop as files were reinstalled.  And, so far, this hard drive isn't grumbling.

THANKS AGAIN AND I WANTED TO POST THIS IN CASE OTHERS HAD A SIMILAR PROBLEM AND WANTED TO KNOW THAT THIS WORKS.

Thanks again.

gm

---

