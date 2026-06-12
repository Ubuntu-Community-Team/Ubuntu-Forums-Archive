---
title: "Xubuntu installation issues"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by allochthonous on 2007-07-04
I am a Linux noob who on occasion has tried a few live CD's and has insatalled various flavors to test out.

A while back I set up a triple boot Win98/Ubuntu 6.10/XP on an old P3 800, 64 MB Radeon 7000, 384 MB of RAM.  I had XP on one HD and Win98/Ubuntu on the other. I booted to the Win98/Ubuntu HD with GRUB as the boot menu.  Now I want to rearrange some things, leaving the XP HD intact,  removing Win98 and installing Xubuntu on the second HD, with a third HD for data (not sure how I am going to partitiion the 3rd drive yet).  

I started the install process last night, but I kept getting an error stating that the partition could not be completely formatted to ext3.  I tried numerous times, using Gparted to tear down the partitions that had been created, leaving all unallocated space on the drive. I then tried to format to ext3 straight from Gparted, but the same error occured.  After several failings, I ran a HD checking utility, and it found no problems with the HD.  I even tested my Xubuntu CD, and again, no errors.

So this morning, I tried a different HD, and used Gparted again to attempt to format to ext3 from an unallocated HD. I received the same error.

I skimmed the forum and found one suggestion of formatting to another format first, then going to ext3. I tried this in Gparted, going first to FAT32, then ext3 and it seemed to work fine.  

After first formatting to FAT32 in Gparted, I ran the installer again, which again failed at the same point.

Next I tried formating to FAT32, then ext3 in Gparted, and installing.  A failure again.

I have never had this much trouble before.  What is going on here?

PK

---

### Post by meborc on 2007-07-04
hmm... this is weird... if you boot the xubuntu cd and start the installation, can you then in the partition manager delete the partitions from the drive you want to use and then choose the FREE SPACE and AUTOMATICALLY PARTITON option? do you still get errors?

i never use gparted... only the ubuntu live cd as it has the partitioning utility built in

just be sure not to erase the partitions/disks you still use

---

### Post by allochthonous on 2007-07-04
I was only using Gparted (within Xubuntu) because the installer partitioner was not working.

Do you mean under one of the "guided" selections or the "manual"?  I assume the manual, as I have been using the guided and have seen no option that specifically says what you have stated.

I can try the manual option and see what happens.

PK

---

### Post by allochthonous on 2007-07-04
OK, i do not understand the "manual" method.

PK

---

### Post by allochthonous on 2007-07-04
Now explain this: 

For kicks, I downloaded and burned Ubuntu and tried the same installation procedure as I have been trying with Xubuntu.  The installer made it through the format just fine and Ubuntu is installing as I type this.

The problem is, I did not want Ubuntu.  I wanted to try Xubuntu since it is more light.

PK

---

### Post by allochthonous on 2007-07-05
Anyone?  Any idea?

PK

---

### Post by acr on 2007-10-16
Have you tried using the alternative Xubuntu CD instead? 
  Sometimes I use the Alternative Install CD instead, runs faster. Does not startup Live preventing some issues such as mounting issues.

---

