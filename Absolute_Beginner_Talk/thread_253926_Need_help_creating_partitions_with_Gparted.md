---
title: "Need help creating partitions with Gparted"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by purplepencil on 2006-09-09
Hi there!

First time poster and complete "n00b". I want to get a dual boot running with Ubuntu and WinXP, just in case there's an annoying piece of software that insists on only working in XP. I want to partition my second hard drive (currently one large NTFS drive) into two partitions, one NTFS, containing all the data currently on there, and the rest as a FAT32 drive, to share files between. I want to set up this partition before I totally reformat my main hard drive to install Windows and Ubuntu, so I've tried using Gparted on the Ubuntu Live CD to resize the NTFS partition and create a FAT32 one with the space that frees up. Trouble is, I go to click "Apply" and a box comes up, and then the program hangs. Nothing happens. The box appears to have two grey progress bars in it, but I can't be sure. Could anyone tell me where I should go from here? I'm not sure how to use Gparted at the command line, but I imagine it might give me some clue as to why things went wrong.

Dave

---

### Post by bulldog on 2006-09-09
Correct me if I'm wrong,but I think you have to unmount the drive you want to change.

But why don't you do so in windows?

---

### Post by bigken on 2006-09-09
It may look as if it is hanging but give it time you must also defrag the drive before you resize it ;)

I would also download the qtparted live disc and use it instead very simple and efective peice of software

---

### Post by purplepencil on 2006-09-09
Thanks for the quick reply guys.

I have somehow managed to aquire a copy of Partition Magic 8, and tried to change the partitions in Windows. Partition Magic rebooted the computer, and then said it couldn't resize the partitions on the second hard drive, because it could not find the Windows partition. Note that the first hard drive, the one I have XP installed on is also divided, it has an old copy of fedora on a partition, and also a FAT32 shared data partition, but it's only 4GB, and I want more than that. Since I believe Ubuntu can read from NTFS, would it be safe to wipe the first hard drive, then after having installed the OSes just create a FAT32 partition using Ubuntu? Then I can copy my data over? It's something I want to avoid, but it looks like my only option. I've tried out a Gparted live cd, I'm not sure whether it's the qparted variety, but that couldn't seem to run. I don't think it could configure the display properly, so it just put me in the terminal... and I have to idea how to partition from there! What do you guys think?

Dave

---

