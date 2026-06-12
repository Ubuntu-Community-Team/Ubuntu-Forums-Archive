---
title: "A few questions"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by k0rn on 2007-05-07
This is a really dumb question and im sure i allready know the answer but just want to make sure. I have a AMD Turion 64 X2 .So i would want to get the Ubuntu 64 AMD platform right? Like i said stupid question and obvious answer i just want to make sure i get the right product. Also i have 960 MB of ram will that be enough ram to dual boot  xp and ubuntu with out slugish results from either OS? And one more question i hope im not asking to much out of this post. My C: drive is a NTFS with 73.2GB free and total size of 99.0 GB. The D: drive is a Fat 32 with 1.31 GB of free space and a total of 11.7GB and is also the hp_recovery drive for re-install of windows. Now the questions is will ubuntu automatic partition the D: drive or the C: drive because obivously the D: has no space on it what so ever. Because if does automaticly try the d: drive then im gonna have to partition it my self with the third option. Sorry for rambling on i just want to make sure i do this right the first time and not the thrid lol. Thank you for any help i can get.

---

### Post by jargoman on 2007-05-07
you can use either the 32 bit x86 or the 64 bit amd_64

you might as well just go with the 64 bit. I think it's like this ubuntu<version>.x86_64 or something similar.

also ubuntu can resize your ntfs partition but I strongly agree that you back up your windows data first as resizing ntfs if difficult because your files are scattered across the drive. It would be a good idea to run defrag one or two times before trying to install. Also check to see if your windows installation disks aren't scratched incase you have to reinstall.

ubuntu installation is pretty straight forward. 

900 megs or ram is more than enough. It doesn't matter if you are dugal booting because you will only run one operating system at a time. If I was to partition manually I would have it look something like this

hda (C: drive)      70 gig
   
hda1        ntfs          /media/hda1          35 (or 40)                     DON'T FORMAT
hda2        ext3         /                                 10                                 format
had2        ext3         /home                       10 (or 15)                    format
hda3        swap       swap                         1gig                              format

hdb

hdb1        fat32        don't mount (leave blank)      all                 DON'T FORMAT

this is only a rough idea. the ubuntu manual installation screen is laid out different. also there are many other way's. this is just what I would do. Also the numbers are a rough estimate as well

---

### Post by jargoman on 2007-05-07
sorry It was spaced out more but for some reason my little chart got scrunched together

---

### Post by k0rn on 2007-05-07
Thank you for answering my questions. I appreciate you takeing the time. And again sorry if they were some dumb questions just want to do it right the first time. Thank you again.

---

### Post by k0rn on 2007-05-07
Im sorry one more question. Do you recommend getting Ubuntu 7.04 Feisty Complete with all the packages? Or just getingUbuntu 7.04 Feisty Desktop and just downloading the packages and updates and such. Thank you.

---

### Post by jonom on 2007-05-07
> **k0rn said:**
> I have a AMD Turion 64 X2 .So i would want to get the Ubuntu 64 AMD platform right?

As jargoman said you can use the 32 or 64 bit versions. 

You may want to try the 32 bit version as compatibility is better.

---

