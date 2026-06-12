---
title: "drive capacity issues"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by ubuntubrian on 2006-08-18
I hope this is ok to post this ? here.
i have a Fantaom drive with 160GB capacity. I have partitioned it into 3 partitions, 2 for Mac and 1 for Ubuntu. The Linux partition is 35GB. I am running out of space on that partition and when I run commands to check the usage and partition size I get conflicting results. The command df -h shows the partition as being 33GB with 25GB used but du -h and the file manager window and Kdistart show 10.9GB used and 4.2GB available. This is a 12GB discrepancy with the actual size of the partiton and the results of the df -h command. I'd love to have those 12gigs but they are nowhere to be found! I've searched hidden directories also.

Thanks for any help.

---

### Post by LadyDoor on 2006-08-18
I don't know whether this was just a typo, but "du" is not a command to show total filesystem usage--it will show you how much space is taken up by whatever dir or file you point it at, and that's it (as far as I know).

---

### Post by ubuntubrian on 2006-08-19
Thanks for the reply. I like your Kaylee avatar! Serenity is great.
Anyway, I used the df command to check all my mounted drives and the one "For_Linux" is shown as having 25GB used out of 33GB space. I used the du command as "du -h /media/For_Linux" which i thought would give me what files and directories were taking up in the "For_Linux" mounted drive. If you know of another command for that purpose I would be most grateful.
Thanks again

---

### Post by LadyDoor on 2006-08-19
Sorry...I think I'm a little confused as to what your goal is. du will tell you, recursively, how much space is taken up...what are you trying to find out with that that is not provided by df?

---

### Post by anaconda on 2006-08-19
And "df -h" rounds the space to closest gigabyte.. If you want accurate numbers use just "df".

if your filesystem type is ext2/3 you can probably get more space by running:

tune2fs -m 0 /dev/'partitions name'

partititons name is hdaX hdbX or sdaX or sdbX... where X is the partitions number..

in ext2/3 quite often 5% of the space is reserved to root user, and by running the above command you adjust it so that 0% is reserved to root..

---

### Post by ubuntubrian on 2006-08-19
Maybe I'm missing something too but the issue is that I am unable to account for 12GB of space on the partition. On the one hand df says I have a 33GB and 25GB used but du says the same partition has only 10.9GB used and 4.9GB available which indicates the partition is only 15GB or so instead of 33GB. All the directories only add up to the 10.9GB so why does df say 25GB are being used out of 33? I know I set up the partitions so that 33GB is the correct partition size and that I only have 10.9GB used so i should have over 20GB available, not 4.9GB.
Any clearer? I hope so.

---

### Post by ubuntubrian on 2006-08-19
Maybe I'm missing something too but the issue is that I am unable to account for 12GB of space on the partition. On the one hand df says I have a 33GB and 25GB used but du says the same partition has only 10.9GB used and 4.9GB available which indicates the partition is only 15GB or so instead of 33GB. All the directories only add up to the 10.9GB so why does df say 25GB are being used out of 33? I know I set up the partitions so that 33GB is the correct partition size and that I only have 10.9GB used so i should have over 20GB available, not 4.9GB.
Any clearer? I hope so. Thanks again.](*,)

---

