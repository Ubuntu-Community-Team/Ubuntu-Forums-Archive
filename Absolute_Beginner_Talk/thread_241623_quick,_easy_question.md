---
title: "quick, easy question"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by blent07 on 2006-08-22
I'm pretty sure I already know the answer, but I'm clarifying it before I give up hope. I want to set up a FAT32 partition on my C drive from the 11gb i have free. Of course, windows is already installed on that drive. I'm pretty sure that there is no way to partition part of a drive WITH an OS installed on it? Is there no way around formatting it? 

Thanks.

---

### Post by Brunellus on 2006-08-22
are you working within Windows or Linux?

There is no "C drive" in Linux.

---

### Post by blent07 on 2006-08-22
I have both installed, using Grub. As of now, I'm working in Ubuntu. But the hard drive I want to partition has Windows on it. It's a 40G hard drive, and i have 11G free that I want to partition away frmo Windows. What I'm hoping is to make a fat32 partition that I can read and write to from both linux and windows.

---

### Post by Jerk on 2006-08-22
Try QTParted.

Here are some instructions. [http://www.help2go.com/Tutorials/Computer_Basics/How_to_Repartition_Hard_Drive_without_Reformatting.html]("http://www.help2go.com/Tutorials/Computer_Basics/How_to_Repartition_Hard_Drive_without_Reformatting.html")

---

### Post by blent07 on 2006-08-22
the QTParted wouldn't allow me to "resize" /dev/hda2, even when I unmounted it, so I found Ntfsresize, which so far is great. However, it tells me I have "at least 1 bad sector" and to run chkdsk  /f /r and reboot twice. I did so and rebooted three times, just to make sure. Back in Ntfsresize, it says the same thing. It says to use the "--bad-sector option" for resizing. Naturally, I can't find anything to do with a "bad sector" option or any other option for that matter. 

Any ideas?

Oh, and the chkdsk went fine.

---

### Post by bodhi.zazen on 2006-08-22
> **blent07 said:**
> the QTParted wouldn't allow me to "resize" /dev/hda2, even when I unmounted it, so I found Ntfsresize, which so far is great. However, it tells me I have "at least 1 bad sector" and to run chkdsk  /f /r and reboot twice. I did so and rebooted three times, just to make sure. Back in Ntfsresize, it says the same thing. It says to use the "--bad-sector option" for resizing. Naturally, I can't find anything to do with a "bad sector" option or any other option for that matter. 

Any ideas?

Oh, and the chkdsk went fine.

ghzaathz ??!!+

That's a "quick, easy question" ?

I do not know the answer so I will not waste your time. I think this is may be a  problem with GParted.

I have problems with GParted and other the re-sizing a Widows partition I would use cfdisk to partition.

Come to think of it, I would use cfdisk to remove Windows.

---

### Post by blent07 on 2006-08-23
once upon a time it was a quick, easy question that i was simply making sure i had right. i was wrong. i'm quickly finding out that if you can dream it, somebody's already got an app to do it.

---

### Post by blent07 on 2006-08-23
Ok, so I found out the --bad-sectors option in Gparted is when you use it via command line, which i found instructions on how to do. All is well except for one wall early on:

I mount the CD ntfsresize is on, and the first thing i'm to do is:

# fdisk -l /dev/hda

so I can retrieve what info I need (what cylinder it starts on, etc.)
But it tells me:

Cannot open /dev/hda

Is it because I unmounted it? I unmounted it cuz i'm pretty sure I couldn't resize the partition if it's mounted? So I mounted hda2 and fdisk gives me:

Unable to open /dev/hda

Any ideas why I can't do fdisk?


Of, and of course all the commands begin with 

./ntfsresize

which is a directory that simply doesn't exist, even when I'm in the directory the CD with gparted is mounted in. I'm beginning to think resizing the ntfs partition isn't worth the trouble...

---

### Post by blent07 on 2006-08-23
well, i figured it out. I had to download something else regarding ntfsresize and use that and i had to do it by command line. So after much reading and some nervous typing, I have a new partition.

thanks for your help.

---

### Post by bodhi.zazen on 2006-08-29
Nice.

---

