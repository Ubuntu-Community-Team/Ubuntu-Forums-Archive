---
title: "Login on a roundabout"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-13
I must be jinxed!:( 

I tried to do a backup with partimage, but it wouldn't work for me, and then I tried ghost4linux and it started to work but then at about 4% done, it said it couldn't contine.  NOW WHEN I REBOOT, I GET THE LOGIN SCREEN, AND WHEN I LOGIN, IT GOES BLACK THE THE LOGIN SCREEN APPEARS AGAIN, AND AGAIN, AND AGAIN......................

So, what can I do about this? 

If I can get Ubuntu working again, I will just leave it alone and not try to alter it in anyway again!  

PLEASE SOMEONE HELP ME!!!

Russty

---

### Post by spur on 2006-09-13
Have you tired to switch off then reboot rather than just reboot. I hav efound this sometimes cleans up a bit more than a simple reboot.Also it could be remembering your past session so choosing a differnt type of session may help.As it is trying to continue on where you left off last time.

---

### Post by Russty of Oz on 2006-09-13
Yes I have tried all that, but still no change.  It began doing this last night, so I turned the computer off and tried today. I have tried  gnome, gnome failsafe and KDE but still nothing. 

Russty.

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> Yes I have tried all that, but still no change.  It began doing this last night, so I turned the computer off and tried today. I have tried  gnome, gnome failsafe and KDE but still nothing. 

Russty.
try this press ctrl+alt+F1 and login using your username now run 
```
sudo /etc/init.d/gdm stop
```to stop gdm now enter ```
startx
```this should start the xserver or at least if it craps out it will give you an error message telling what caused the xserver not to startup.

---

### Post by Russty of Oz on 2006-09-13
well I got the following message,

**X session: warning:  unable to write to /tmp;  X session may exit with an error**


So where to now?

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> well I got the following message,

**X session: warning:  unable to write to /tmp;  X session may exit with an error**


So where to now?

the permissions or ownership of /tmp have got changed try this no gurantees though
```
sudo chown root:root /tmp
```
then
```
sudo chmod 1777 /tmp/
```
and try starting x again with 
```
startx
```

---

### Post by Russty of Oz on 2006-09-13
It actually started in Xfce.  But nothing in it works except the terminal.

I posted this BEFORE I read your last reply, so this has nothing to   do with that.  I will now try what you suggested.

---

### Post by Russty of Oz on 2006-09-13
I got the following from that;

[B]Error opening /dev/wacom : No such file or directory
(EE) Xf86OpenSerial: Cannot open device /dev/wacom
     No such fil or directory

waiting for X server to shut down FreeFontPath : FPE "/usr/share/X11/fonts/misc"
refcount is 2, should be 1; fixing.[/B]

Means nothing to me!

Russty

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> I got the following from that;

[B]Error opening /dev/wacom : No such file or directory
(EE) Xf86OpenSerial: Cannot open device /dev/wacom
     No such fil or directory

waiting for X server to shut down FreeFontPath : FPE "/usr/share/X11/fonts/misc"
refcount is 2, should be 1; fixing.[/B]

Means nothing to me!

Russty

i get the same errors about /dev/wacom im assuming it's because i don't have a wacom tablet attached, i have no clue about the font path error though.
did you restore from a corrupt backup or did the error happen while you were making a backup?

---

### Post by Russty of Oz on 2006-09-13
it happened while making the backup.  The backup failed to complete, so this is what it somehow did to my installed Ubuntu.  

I hope I can get it working again, seeing as I don't have a backup.

Russty.

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> it happened while making the backup.  The backup failed to complete, so this is what it somehow did to my installed Ubuntu.  

I hope I can get it working again, seeing as I don't have a backup.

Russty.
have you tried restarting after you changed the permissions of /tmp to see if it works?

---

### Post by Russty of Oz on 2006-09-13
Tried that, still doesn't work.

Round and round we go!

Russty

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> Tried that, still doesn't work.

Round and round we go!

Russty

i wish i knew how to help you fix it but im kind of stumped here. if it were me, i would boot up using the livecd mount my ubuntu partition and copy all my data to my external harddrive or over my network and reinstall, beacuse a clean install only takes about 8 minutes on my computer and trouble shooting this could take days.

---

### Post by Russty of Oz on 2006-09-13
Now that sounds very interesting!!

The only thing is, after I reboot with the live cd, how do I mount my ubuntu partition?  

That sounds like the best solution.

Russty.

---

### Post by codejunkie on 2006-09-13
> **Russty of Oz said:**
> Now that sounds very interesting!!

The only thing is, after I reboot with the live cd, how do I mount my ubuntu partition?  

That sounds like the best solution.

Russty.

when you get to the desktop using the livecd open a terminal and run ```
sudo fdisk -l
```it will list all the partitions you have on your disk like this
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9587    77007546   83  Linux
/dev/hda2            9588        9964     3028252+   5  Extended
/dev/hda5            9588        9964     3028221   82  Linux swap / Solaris

``` 
so on mine the ubuntu partition is /dev/hda1 now that i know what the drive number is create a mount point with ```
sudo mkdir /mnt/ubuntu
```now mount the partition with ```
sudo mount /dev/hda1 /mnt/ubuntu
```and run last run ```
sudo nautilus /mnt/ubuntu
```this will open a root nautilus window that allows full access to the data so i can  archive it or just move it over to my external hd.

---

### Post by Russty of Oz on 2006-09-13
Thanks codejunkie, I will give that a try later or tomorrow morning, it is getting late here in Oz, and my eyes are going square after spending all afternoon on this.

You have been very helpful with all this and I apreciate everything you have done to help. I will let you know what happens, so have a look at this thread tomorrow.

Russty.

---

### Post by Russty of Oz on 2006-09-14
OK, I found what was causing the problem.  It was because the Ubuntu partition was FULL!!  It seems that when I attempted the backup, it was sending the backup to the Ubuntu partition.:redface:   I am sure I selected another partition, but that is what it did.  I found that the partition was full by mounting the partition as mentioned by codejunkie, so then I found how to resize the partitions with gparted on the live CD and that was it!!  So now Ubuntu boots again!  

Thanks codejunkie for the help, I couldn't have got my Ubuntu back without your expertise.

Russty. :)

---

