---
title: "install using existing partitions"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-06-22
Used the above as a search term and found no answers, so ...

I'm trying to install Dapper with the alternate CD. I've already got Breezy there. According to the installer, my existing partitions are:

#1 primary B K ntfs /media/hda1
#2 primary    K ext3 /media/hda2
#5 logical     F swap swap
#6 logical     K fat32 /media/hda6
#7 logical     K ext3 /media/hda7 

And I don't want to change anything. Apologies for what is probably a stupid question, but can I just hit "Finish partitioning and write changes to disk"? Or do I have to "resize" something?

---

### Post by frodon on 2006-06-22
If this partition table fits your needs you can hit "Finish partitioning and write changes to disk", you would have to resize a partition only if this partition table didn't correspond to what you want.

---

### Post by adam.tropics on 2006-06-22
You have no paritions ready to go yet as you need a root partition at least and a home partition as well preferably. (You already have swap) What sizes are the ext3 partition (assuming you want to keep the windows stuii you have)?

---

### Post by editrix on 2006-06-23
First off, thanks muchly for the quick reply--I tried to respond yesterday, but my ISP is having all kinds of web problems.

[QUOTE=adam.tropics]You have no paritions ready to go yet as you need a root partition at least and a home partition as well preferably. (You already have swap) What sizes are the ext3 partition (assuming you want to keep the windows stuii you have)?[/QUOTE]

Well, I thought I did, since the drive was already formatted for Breezy, but when I hit Finish partitioning it told me I had no root partition. So I changed hda2 from /media/hda2 to / (i.e., root) but now when I hit Finish partitioning nothing happens.

Okay, I see I *also* have to format it as ext3, even though it already is formatted as such.

For the benefit of others who may be searching for this info:

Breezy installed on a dual-boot, now installing Dapper.
1. I did NOT reformat any of my other partitions--just the hda2, which was the root partition in my Breezy installation.
2. After reformatting hda2, I hit Finish partitioning
3. Went to make some coffee.
4. Installed Grub boot loader when it asked me to, although it was already installed.
5. Got the Installation Complete message--hit Continue.
Oh my, Ubuntu is pretty!
6. My Home folder has been wiped but the fat32 partition (/media/hda6) I created to share files between Win & Lin is just fine.
7. Verified XP still runs okay. It does.
8. Now, on to setting up email, keyboard shortcuts, etc. (and changing my sig)

---

### Post by adam.tropics on 2006-06-24
For future reference, if you keep /home on a seperate partition, then re-installing will not require you to format the /home partition and you will keep  your files! If you just use a folder for /home then you will need to remember to backup because a fresh install will wipe it.

---

