---
title: "Linking to another partition"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by icedcheese on 2006-11-06
Hi All!

I was wondering if someone is able to assist me.

I have 2 partitions on my PC, one with Ubuntu on it, and the other which I store my files on.

At the moment, I can link to the partition with the files on it through the Administration - Disks, however everytime I reboot I need to do this again to ensure that I can link to the files again.

Is there a way I can make it so the link to my files partition stays there, even when I reboot?

Thanks
Michael

---

### Post by kvonb on 2006-11-06
Hello,

What type is your file storage?  Windows or Linux?

Try this link below, search the page for 'mount' or 'partition', it is an excellent site with tons of useful info.

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

If you can't get by with that, re-post here and me or someone will try to help you further.

Regards,  Kev :D

---

### Post by icedcheese on 2006-11-06
Hi Kev

Thanks for your help!  I checked out the ubuntu guide but was unable to find the right information.  The funny thing about this problem is I have worked it out before, but it has since slipped my mind!

The other partition is Linux - its an Extended 3.

I do recall editing a file and adding a new line in to link to the partition through the terminal.

Thank you so much for your help.

---

### Post by icedcheese on 2006-11-06
Hi There!

Problem solved, I used the following command to do it:

sudo mkdir /files
sudo mount -t ext3 /dev/hda2 /files

Thank you so much for the quick response to my problem!

---

### Post by bodhi.zazen on 2006-11-06
> **icedcheese said:**
> Hi There!

Problem solved, I used the following command to do it:

sudo mkdir /files
sudo mount -t ext3 /dev/hda2 /files

Thank you so much for the quick response to my problem!

To have the partition avaliable on boot you need to edit fstab:

[How to fstab](http://ubuntuforums.org/showthread.php?t=283131)

---

