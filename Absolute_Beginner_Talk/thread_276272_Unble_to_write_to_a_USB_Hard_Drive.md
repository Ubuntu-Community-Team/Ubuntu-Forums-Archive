---
title: "Unble to write to a USB Hard Drive"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by beagle on 2006-10-12
I have a new 40Gb (Maxtor) External hard drive connected through USB.
The drive icon shows up on my screen. But I am unable to write to it.
I get the following error:

Error while copying to '/media/usbdisk'. You do not have permissions to write to this folder.

If try to change the folder's properties -> permission, it prompts me that it is read 'only drive'
I searched through your forum for answer but couldn't find.
Please help me to use this external drive.  Thanks in advance.

---

### Post by Iarwain ben-adar on 2006-10-12
Hi,
Isn't there some sort of write-protection enabled?

The hardware kind i mean,
because yesterday i experienced a similar problem, and found out it 
was due to my mp3-player that was on "hold" ..

Other than that, i wouldn't know :?


Iarwain

---

### Post by Ronin1970 on 2006-10-12
What filr format is the drive?

---

### Post by beagle on 2006-10-13
The file format is Windows NTFS.
It is not allowing me to change read/write permissions.

---

### Post by Iarwain ben-adar on 2006-10-13
Hi,
maybe you can try [this](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)


Iarwain

---

### Post by luckylucky on 2006-10-13
There are two likely reasons for your experience:
1) Your HDD is in an NTFS format
2) (and/or) You are trying to write to it from the "live" demo version of Ubuntu

Here are solutions for the above two reasons:

1)  You could try that program that someone else linked to which will allow you to write to NTFS partitions, however it is still "experimental software", and so thus it might not be the best solution.  I'd recommend (if you don't already have important data on it) that you format the HDD drive to FAT32, or even split up the hard drive to have half the drive partitioned to FAT32 so that you could use it on both windows and linux machines.  My favorite formatting and partitioning tool is "GParted".  Download the program and find a tutorial on how to use it in google.

2)  If you are trying to write to your hard drive but you are in the "live" demo version of Ubuntu know that it won't allow you to do that.  The developers have built in the safety feature of preventing writting to hard drives in the demo version so that you can play around with Ubuntu without any fears of risk of damaging your data.  If you need to copy files from a live demo Ubuntu session then put it on a USB flash key, or email it, or you may also transfer files through the Internet or your home network.

Hope this might have helped you.

---

### Post by beagle on 2006-10-13
All of your fast responses really helped me to experiment several methods.
Earlier, I was quite disappointed, when I called the manufacturer's (Maxtor) tech support.  When I told them that my machine runs on Linux, they simply said that they don't support it and stopped the conversation.

Finally here is how I got it working.
One good thing that it was a brand new drive (maxtor onetouch III, 40gb external usb drive); didn't worry about loosing data.

Unmounted the drive.
I went to terminal mode and became 'su'.
formatted the drive with the command:

mkfs.ext3 -j /dev/sda1

Then changed the drives permission to regular user.
Now everything works.

Thanks for all your help.

---

### Post by stoeptegel on 2006-11-17
> **beagle said:**
> When I told them that my machine runs on Linux, they simply said that they don't support it and stopped the conversation.

That will be maxtor on my personal blacklist then.

> 
Then changed the drives permission to regular user.
Now everything works.


Good to hear that.

---

### Post by drogers on 2007-07-05
> **beagle said:**
> All of your fast responses really helped me to experiment several methods.
Earlier, I was quite disappointed, when I called the manufacturer's (Maxtor) tech support.  When I told them that my machine runs on Linux, they simply said that they don't support it and stopped the conversation.

Finally here is how I got it working.
One good thing that it was a brand new drive (maxtor onetouch III, 40gb external usb drive); didn't worry about loosing data.

Unmounted the drive.
I went to terminal mode and became 'su'.
formatted the drive with the command:

mkfs.ext3 -j /dev/sda1

Then changed the drives permission to regular user.
Now everything works.

Thanks for all your help.

i'm a complete noob so i don't understand this... i have the same problem as this
guy... or the same problem that this guy _had_ anyway...
I have the same drive (Maxtor OneTouch III USB) though mine is an 80g but i don't think that
makes a difference...
i'm running a live cd because i messed up my ubuntu ultimate badly and i really really need
the info on the that hard drive (all my work documents)... I plugged the drive into my home
computer (xp pro) and worked fine... i plugged it into my laptop (ubuntu live) and it recognizes
it and i can read all the files but not write anything to the drive...
anyone have a simple step by step? if i can't get these files off i'm really screwed!

---

### Post by drogers on 2007-07-05
anyone?

---

### Post by fedira on 2007-07-05
Hey drogers -- I don't know much, but luckylucky already responded to your issue [above]("http://ubuntuforums.org/showpost.php?p=1613492&postcount=6"). You can't write to any hard drives while running Ubuntu Live:

> If you are trying to write to your hard drive but you are in the "live" demo version of Ubuntu know that it won't allow you to do that. The developers have built in the safety feature of preventing writting to hard drives in the demo version so that you can play around with Ubuntu without any fears of risk of damaging your data. If you need to copy files from a live demo Ubuntu session then put it on a USB flash key, or email it, or you may also transfer files through the Internet or your home network.

If you can access the files on your Maxtor from your home computer anyway though, I don't understand why this is a crisis. ?

---

### Post by drogers on 2007-07-05
well that's no good...

my laptop which has ubuntu crapped out on me and i need to grab the files off of there...
i just plugged in the usb drive into my windows box at home to see it... that's all...

---

### Post by Ripfox on 2007-07-06
Figure out what your external drive is named, (/dev/sdb ect...) 

then do his command replacing with your drive name

---

### Post by Homey on 2007-08-05
I had the same problem
My USB external Harddisk (Fat32) was working normally in both Vista and Ubuntu but since yesterday I noticed that I can't write to it in Ubuntu any file or folder it's just "read only" .. I tried everything on ( properties/permissions)  but no resault .. writing any file to it , I got " **you do not have permissions to write to this folder**"

the only way I got it work again is to install gParted from synaptec then from the gParted I've chosen my usb drive , right click on it and I unmount it .. after 2 minutes of operation , I turnd off the usb drive and then trund on ...  it's working again with full access (read + write)

---

