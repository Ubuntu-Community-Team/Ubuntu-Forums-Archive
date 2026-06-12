---
title: "Installing Ubuntu, choosing partition?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by badmephisto on 2007-04-19
I decided to switch to Linux finally a few weeks ago. My friend made a separate partition from my Windows partition, and installed Fedora Core on it. Now i'd like to put Ubuntu 7.04 over on that same partition, erasing Fedora, but im mortally afraid that ill accidentally install over my windows partition and loose my files.

I got stuck on step 4/7 of the installation... It says "How do you want to partition the disk?" and i can choose from:
Guided - resize SCSI1 (0,0,0) partition #2 (sda) and use freed space
Guided - use entire disk
Guided - use largest continuous free space
Manual

I have no idea what any of the above mean... Can anyone help me out?

---

### Post by aysiu on 2007-04-19
You want Manual.

If you want more guidance than that, paste (do not retype) this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back into this thread: ```
sudo fdisk -l
```

---

### Post by bobplano on 2007-04-19
> **badmephisto said:**
> I got stuck on step 4/7 of the installation... It says "How do you want to partition the disk?" and i can choose from:
Guided - resize SCSI1 (0,0,0) partition #2 (sda) and use freed space
Guided - use entire disk
Guided - use largest continuous free space
Manual

I have no idea what any of the above mean... Can anyone help me out?

well the first one is you are resizing one of your partitions to make room for ubuntu
the second one erases and uses your entire disk
the 3rd one uses the biggest free space
the manual one allows you to adjust the partitons yourself. 

i would go with the manual one if you know what all the partitions are that you are changing are. you can also just go manual and look to see which partitions you want then the next step is choosing which partittions to use and then you can choose to reformat the fedora core ones

---

### Post by Comzee on 2007-04-19
> **bobplano said:**
> well the first one is you are resizing one of your partitions to make room for ubuntu
the second one erases and uses your entire disk
the 3rd one uses the biggest free space
the manual one allows you to adjust the partitons yourself. 

i would go with the manual one if you know what all the partitions are that you are changing are. you can also just go manual and look to see which partitions you want then the next step is choosing which partittions to use and then you can choose to reformat the fedora core ones

If you don't want to delete anything and don't have any unpartitioned space, well your screwed.
If you have unpartitioned space, set one partition for Linux-swap with a size of 1gb. Use the rest of the space for am EXT3 partition. Proceed to the next step. Only choose the two new partitions that you just created to use. Thats what I did to use dual boot.

EDIT: Thats using the manual setup option.

---

### Post by badmephisto on 2007-04-19
hey thank you for reply. I am on my desktop with my laptop next to me, and this dekstop is running windows so i cant paste the output back to you... but after running the command I see that i have 6 partitions. sda1,2,3,...6. 

sda1 is dell utility, it has only 49 MB so that isnt it for sure

sda2 is my windows partition im pretty sure, since its ntfs
sda3 i have no idea what is.... Id is "db", and System is "CP/M / CTOS/ ... it is fat32 and has 3.2 GB, used 2.6GB
sda4 i think it says is unusable. Id is 5, System is "Extended"
sda5 has Id "83", and System is "Linux". Its size is106 MB, used 18MB
sda6 finally has Id "8e", System "Linux LVM", it has 30GB and used is Unknown

i am no expert but i think sda6 is what i want, because i vaguely remember partitioning my HD as about 30GB to my Fedora core.

---

### Post by badmephisto on 2007-04-19
im installing it on the 30GB partition. god help me

---

### Post by badmephisto on 2007-04-19
i have another problem :-\ I have to choose Type and Mount point. What are those... I tried Type as fat32 and mount point /
but that didnt do it:

The file system fat32 cannot be mounted on /, because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2

??:(

---

### Post by aysiu on 2007-04-19
Choose Ext3 for the mount point / and choose to reformat it

For the Windows partition, you can mount it to /media/windows and choose **not** to reformat it.

---

### Post by Anskire on 2008-07-18
Ok dudes i have recently decided to bite the bullet and give ubuntu a try

i currently have three partitions on my laptop HD in windows at least   c,d,e

both c and d are roughly 8 gig and the other one is 60

currently i have win xp installed on my c drive and i want to install ubuntu onto my other 8 gig partition which is D

How can i do this?

When i click on manual it takes me to the partition manager which is fine and i can see the three discs 

the first one which has my copy of windows the second which i belive to be my other 8 gig and the thrid which is my 60

but when i click on the format button and set the type to ext3 i get an error that roughy moans about the root or boot being undifined 

can someone plz give me a step by stepof how i can install onto my second 8 gig partition

---

