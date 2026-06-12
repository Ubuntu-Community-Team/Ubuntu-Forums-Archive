---
title: "I don't understand &quot;Partitioning&quot;"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Douglas B. on 2007-02-22
Hi Guys
I guess if you have created partitions on a hard drive before it doesn't seem very hard; but I have never done it. And i'm running into a problem. 
I have an Acer 9300-5024 laptop with a 160 GB hard drive. I have downloaded both 6.06.1 LTS and 6.10. I ran "Check CD for defects" and both disks are OK. Both disks run fine from the CD. 
Everything goes fine when I click Install untill it gets to the options. As it is switching from the "Who are you?" page to the "Prepare disk space" page there is a quick desplay stating that I will be able to choose three options; but when the "Prepair disk space" page opens there are only two options.

Erace entire disk, and Manually edit' 

The first option, "Resize IDE1master,partition#1[hdal]and use free space isn't there at all.
I tried the 6.10 disk first and then the 6.06. It was the same on both disks. 
I have no idea how to do it manually.
If I have to do it this way does anyone know a site that will give me step by step instructions? 
Thanks again guys
Doug

---

### Post by Shatrat on 2007-02-22
First make sure you defrag in windows to minimize the chance of something going wrong with your NTFS filesystem.
Then when you are in the manual partition editor, first resize /dev/hda1  down to  whatever size you are comfortable.
Then you make a New small partition 1.5 times larger than the ammount of RAM you have and use linux-swap as the filesystem.
Then use the rest of the space for an ext3 partition.

On the next screen after the partitioner I blieve it will ask you for mount points.  the small partition you made is going to be swap and the larger one is /

---

### Post by Duck2006 on 2007-02-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

