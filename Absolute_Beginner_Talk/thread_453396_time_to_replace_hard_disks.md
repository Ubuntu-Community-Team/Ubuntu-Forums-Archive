---
title: "time to replace hard disks"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Farhan on 2007-05-24
due to some power failure and fluctuations, my current hard disk is making loud noises and i thought that it is high time that i replace it with a new one. now, my question is, what should i do to keep my current installation of Feisty (with all the softwares i installed and tweaks i have made) intact and copy everything to the new hard disk so that it would boot like as if nothing happened? is it possible? if yes, any pointers anyone?

thanks in advance.  :)

PS. i am just changing the hard drive. all other hardware is going to be the same.

---

### Post by lamalex on 2007-05-24
check out g4l (ghost 4 linux) also you could just dd the who image, but that is a little bit less than elegant and can mess things up if your new drive has a differen block size etc... Look into G4L.

---

### Post by edwardLS on 2007-05-24
I use Acronis True Image to perform disk/partition cloning such as what you are doing.  However, it is a commercial products, and some in the Open Source community don't want any commercial/proprietary software.  I need it for work I do with the various Windows version, but True Image also understands the various Linux File Systems such as 'ext3'.  

True Image has save my bacon more times than I can count in both Windows and Linux.

---

### Post by onbongos on 2007-05-24
aptoncd will make a cd of your packages and you could just burn your home folder

---

### Post by Atomic Dog on 2007-05-24
I also use Acronis True Image.  It is not that expensive and will save your bacon, as it has also saved mine on a couple of occasions.  I think it costs less than $30 and is well worth the price IMHO.  The bootable CD that you create to create/restore images (with a usb drive for instance) is the shiznit!

---

### Post by cwmoser on 2007-05-24
Will Norton Ghost image a Linux partition?

Carl

---

### Post by edwardLS on 2007-05-24
I had used Norton Ghost at one point in the past, and it was difficulty I was having with Norton Ghost and Linux (Red Hat and Linspire at that time) that caused me to give Acronis True Image a try.  

As I recall ( I do suffer from CRS) I was able to image the Linux partition(s), but when I restored them I had some problem that resulted in my having to re-install the Linux system.  After all, a backup program should only be evaluated on its "Restoration" capabilities.  I may having been something wrong with Norton Ghost, but I quickly reached my frustration level. 

Been using Acronis True Image and Acronis Disk Director Suite ever since, and I haven't looked back.

---

### Post by Farhan on 2007-05-24
wow! so many replies in such a short time! thanks everyone for replying. as a new user, i must admit that this community is awesome. great to be a part of it. now back to business:

1. i could not use Acronis TrueImage or Ghost4Linux because my older harddrive was 160GB and this one is 80GB. there isn't simply enough space to backup and restore. the point is that both the harddrives must have same amount of space? not my option i guess! :(

2. so i have installed a fresh copy of Fiesty on my new harddrive and right now i am using the new installation, from where *i can see all my old data*. so that is good news i believe. what could be done from this point to make things exactly like it was in my other installation? i could just copy EVERYTHING on "/" on the old disk to the new disk and it would work?

3. tried and created an ISO with APTonCD and even restored the files in the new installation, but don't really know what happened to them? they never got installed! do i have to go and manually install all of them with "sudo dpkg -i *.deb" or there is another way?

4. this must be redundant after question 2 but just copying the old /home to the new /home will be enough to migrate? nothing else?

thanks for replying with such speed guys. really appreciate it.

---

### Post by ramjet_1953 on 2007-05-25
I agree with lamalex.

Ghost for Linux (G4L) works great, even cloning to a USB drive.

It makes an exact 1:1 copy, including GRUB. All you do is then install the cloned drive and away you go.

Regards,
Roger :cool:

---

### Post by Atomic Dog on 2007-05-25
The new drive is 1/2 the size?  How do you expect to fit 160GB of data onto an 80 gb drive?  As long as a drive  image totals less GB than the drive you are cloning it to, then it will work.

---

