---
title: "Ubuntu &amp; Windows"
date: 2005-07-31
forum: Absolute Beginner Talk
---

### Post by cadaver on 2005-07-31
[FONT=Courier New]I want to install Ubuntu w/o deleting Windows. During installation, what should I select?[/FONT]

---

### Post by jasmuz on 2005-07-31
You would need to resize your Windows partition in order to make the partition for / and for swap.

---

### Post by Irony on 2005-07-31
First you have to back up all your files in windows, then you need to defragment your drive. Do the defragment twice, basically try to squash all the files to the beginning of the drive as much as possible.

Then look at [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html) note its 3 pages of screen pictures. What he does is shrink his ntfs partition thus allowing a big free space on which ubuntu can be set to automatically partition and install on.

Note ubuntu in automatically partitioning creates main partition and a swap partition. I've tried it and it works.

Note that you must have enough space on your drive to do this and the files must be defragged as much as possible or you can lose files.

---

### Post by mental_noise on 2005-08-01
Hello. im new in using Ubuntu, or Linux in general. I'm currently on Windows XP and I would like to try Ubuntu Linux.  I've tried the Live CD my friend gave me and I was amazed with it.  Now, I want to install it to my PC but since I am still learning, I don't want to erase Win XP just yet.

I already have two partitions in my HD (C:\ and D:\).  What I would like to know is if I installed the Ubuntu OS onto the D:\ drive, will it affect my Win XP installation which is installed in the C:\ drive? :roll:

---

### Post by odin on 2005-08-01
[QUOTE=mental_noise]Hello. im new in using Ubuntu, or Linux in general. I'm currently on Windows XP and I would like to try Ubuntu Linux.  I've tried the Live CD my friend gave me and I was amazed with it.  Now, I want to install it to my PC but since I am still learning, I don't want to erase Win XP just yet.

I already have two partitions in my HD (C:\ and D:\).  What I would like to know is if I installed the Ubuntu OS onto the D:\ drive, will it affect my Win XP installation which is installed in the C:\ drive? :roll:[/QUOTE]


If you dont have any windows aplication installed in d: then you just back up all the data you have there(I guess that other partition was for your music etc.)and you shouldn't have any problem with your windows partition.Remember that you also need some space for the swap. :grin:

---

### Post by phen on 2005-08-01
and remember the disk/partition sizes, so that you do not delete the wrong one....

---

### Post by damaged on 2005-08-01
[QUOTE=mental_noise]Hello. im new in using Ubuntu, or Linux in general. I'm currently on Windows XP and I would like to try Ubuntu Linux.  I've tried the Live CD my friend gave me and I was amazed with it.  Now, I want to install it to my PC but since I am still learning, I don't want to erase Win XP just yet.

I already have two partitions in my HD (C:\ and D:\).  What I would like to know is if I installed the Ubuntu OS onto the D:\ drive, will it affect my Win XP installation which is installed in the C:\ drive? :roll:[/QUOTE]
 I recently did the change from Windoze 2000 to Ubuntu. I had a small 13GB hard drive that I used to have music on. I shifted the music to my 40GB drive, then formatted the 13GB drive and installed Ubuntu on it. Win2K was still on my 40Gb drive. I then mounted the folders I still needed from the Win2K drive. Win2K still works (although I've hardly used it since I installed Ubuntu). 

It is a good idea before making the change from Windows to start using as much FS on Windoze as possible (Firefox, Thunderbird, OpenOffice etc.) that way you will have less of shock coming across to Ubuntu.

---

