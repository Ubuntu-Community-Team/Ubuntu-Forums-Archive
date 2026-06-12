---
title: "Mythbuntu and external USB drive"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by ShaneJohnson on 2007-11-13
Firstly I am new to Linux and apologise if this is already posted...could not find anything close to my issue.

I installed Ubuntu 7.10 and Mythbuntu and both are running perfectly with internet connect.   So no software dramas.

I have an external USB HD 320GB attached which I can access via the Ubuntu desktop with no dramas.

On this HD are my kids DVDs ie. folder with movie name and TS-Video folders and VOB files.

My question, and there is one.....I am unable to find out how to tell Mythbuntu to look in the external drive for the dvd files in the setup options.   Each combination I try simply shows as 'no videos' in Myth.

Thanks.

---

### Post by ubnewbie2 on 2007-11-13
Try mounting the external drive to a directory under the one that myth is currently using for video storage.  If I remember correctly, with myth, you have to then get it to reread or scan for new videos.

---

### Post by newlinux on 2007-11-14
Yes, by default myth will only look under one directory tree for videos (wherever it is configured to look) and it must be scanned with video manager whenever there are updates to see the new videos. You can (somewhere in the setup menu) have myth browse files that haven't been scanned in in the video directory tree (so you can bypass the video scan when adding new content).

---

### Post by ShaneJohnson on 2007-11-15
Thanks...I got the USB to mount and modified the fstab file to auto mount.     I am still having trouble telling Mythbuntu to look in the external HDD for the files.  

The mounted drive was :   /dev/sda1 /mnt/usbhdd      

On the usb drive is a parent folder called movies->[movie_name] folder->TS Video->[vob files etc].

---

### Post by newlinux on 2007-11-15
so what did you try to get myth to scan the external HDD? did you tell it to look in /mnt/usbhdd/ and then go to video manager and scan?

---

### Post by ShaneJohnson on 2007-11-15
I cannot find an option in Mythbuntu to scan for movies?   Excuse my ignorance.

---

### Post by ShaneJohnson on 2007-11-16
Worked out how to scan.....the problem seems to be I have not got Mythbuntu to look in the right place......is this right in the 'Directory that holds videos:' option -

/dev/sda1 /media/usbhdd/movies

'movies' is name of the harddrive the movie folders are in.   External HDD is showing as mounted (I'm guessing as the is an option to unmount when I right click on the icon).

---

### Post by ShaneJohnson on 2007-11-16
Folks.....thankyou for the help....the suggestions have given me something to work on.....have solved the whole issue and all is working fine.     Thanks again.

---

